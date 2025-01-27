<template>
    <BaseLayout>
        <div class="flex items-center justify-center  min-h-screen sm:max-w-[690px] lg:max-w-[710px] mx-auto p-4">
            <div v-if="setting != null" class="w-full">
                <div v-if="!isLoadingWallet"
                    class="flex flex-col w-full bg-gray-200 hover:bg-gray-300/20 dark:bg-gray-800/50 p-4 rounded hover:dark:bg-gray-900"
                    style="background-color: var(--navtop-color-dark);">

                    <div v-if="setting != null && wallet != null && isLoading === false"
                        class="flex flex-col w-full p-4 rounded ">
                        <form v-if="wallet.currency === 'BRL'" action="" @submit.prevent="submitWithdraw">
                            <div class="flex items-center justify-between">
                                <p class="text-gray-500">{{ $t('Withdraw Coin') }}</p>
                                <button @click.prevent="$router.push('/profile/wallet')" type="button"
                                    class="flex justify-center items-center mr-3 pt-1">
                                    <div>{{ wallet.currency }}</div>
                                    <div class="mr-2 ml-2">
                                        <img :src="`/assets/images/coin/` + wallet.currency + `.png`" alt="" width="32">
                                    </div>
                                    <div class="ml-2 text-sm">
                                        <i class="fa-solid fa-chevron-down"></i>
                                    </div>
                                </button>
                            </div>

                            <div class="mt-5">
                                <p class="mb-2 text-gray-500">{{ $t('Withdraw with') }}</p>
                                <div
                                    class="w-full flex items-center justify-between bg-white dark:bg-gray-900 rounded p-2">
                                    <div class="flex w-full items-center">
                                        <img :src="`/assets/images/pix.png`" alt="" width="100">
                                        <span class="ml-3">PIX</span>
                                    </div>
                                    <div class="w-8 ">
                                        <i class="fa-solid fa-chevron-down"></i>
                                    </div>
                                </div>
                            </div>

                            <div class="mt-5">
                                <div class="dark:text-gray-400 mb-3">
                                    <label for="">Nome do titular da conta</label>
                                    <input v-model="withdraw.name" type="text" class="input w-full p-2 text-sm sm:text-base"
                                        placeholder="Digite o nome do titular da conta" required>
                                </div>
                            
                                <div class="dark:text-gray-400 mb-3">
                                    <label for="">Chave Pix</label>
                                    <input v-model="withdraw.pix_key" type="text" class="input w-full p-2 text-sm sm:text-base"
                                        placeholder="Digite a sua Chave pix" required>
                                </div>
                            
                                <div class="dark:text-gray-400 mb-3">
                                    <label for="">Tipo de Chave</label>
                                    <select v-model="withdraw.pix_type" name="type_document" class="input w-full p-2 text-sm sm:text-base" required>
                                        <option value="document">CPF/CNPJ</option>
                                        <option value="email">E-mail</option>
                                        <option value="phoneNumber">Telefone</option>
                                        <option value="randomKey">Chave Aleatória</option>
                                    </select>
                                </div>
                                
                            
                                <div class="dark:text-gray-400 mb-3">
                                    <div class="flex justify-between mb-3 text-sm sm:text-base">
                                        <p>Valor ({{ setting.min_withdrawal }} ~ {{ setting.max_withdrawal }})</p>
                                        <p>Saldo: {{ state.currencyFormat(parseFloat(wallet.balance_withdrawal), wallet.currency) }}</p>
                                    </div>
                                    <div class="flex flex-wrap bg-white dark:bg-gray-900 rounded-md">
                                        <input type="text" class="input w-full sm:flex-grow p-2 text-sm sm:text-base border-r border-gray-300 dark:border-gray-700"
                                            v-model="withdraw.amount" :min="setting.min_withdrawal" :max="setting.max_withdrawal" placeholder=""
                                            required>
                                    </div>
                                    <div class="flex justify-between mt-2 text-sm sm:text-base">
                                        <p>{{ $t('Available') }}: {{ state.currencyFormat(parseFloat(wallet.balance_withdrawal), wallet.currency) }}</p>
                                        <p>{{ $t('Balance Rollback') }}: {{ state.currencyFormat(parseFloat(wallet.balance_bonus), wallet.currency) }}</p>
                                    </div>
                                </div>
                            
                                <div class="mb-3 mt-5">
                                    <div class="flex items-center mb-4">
                                        <input id="accept_terms_checkbox" v-model="withdraw.accept_terms" type="checkbox" value=""
                                            class="w-4 h-4 text-green-600 bg-gray-100 border-gray-300 rounded focus:ring-green-500 dark:focus:ring-green-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600">
                                        <label for="accept_terms_checkbox" class="ms-2 text-sm sm:text-base font-medium text-gray-900 dark:text-gray-400">
                                            {{ $t('I accept the transfer terms') }}
                                        </label>
                                    </div>
                                </div>
                            </div>
                            

                            <div class="mt-5 w-full flex items-center justify-center">
                                <button type="submit" class="ui-button-blue w-full">
                                    <span class="uppercase font-semibold text-sm">{{ $t('Request withdrawal') }}</span>
                                </button>
                            </div>
                        </form>

                    </div>

                    <div v-if="isLoading" role="status"
                        class="absolute -translate-x-1/2 -translate-y-1/2 top-2/4 left-1/2">
                        <i class="fa-duotone fa-spinner-third fa-spin"
                            style="font-size: 45px;--fa-primary-color: var(--ci-primary-color); --fa-segundary-color: #000000;"></i>
                        <span class="sr-only">{{ $t('Loading') }}...</span>
                    </div>

                </div>
            </div>
        </div>
    </BaseLayout>
</template>


<script>

import { RouterLink, useRouter } from "vue-router";
import BaseLayout from "@/Layouts/BaseLayout.vue";
import WalletSideMenu from "@/Pages/Profile/Components/WalletSideMenu.vue";
import HttpApi from "@/Services/HttpApi.js";
import { useToast } from "vue-toastification";
import { useSettingStore } from "@/Stores/SettingStore.js";


export default {
    props: [],
    components: { WalletSideMenu, BaseLayout, RouterLink },
    data() {
        return {
            isLoading: false,
            setting: null,
            wallet: null,
            withdraw: {
                name: '',
                pix_key: '',
                pix_type: 'document',
                amount: '',
                type: 'pix',
                currency: '',
                symbol: '',
                accept_terms: false
            },
            withdraw_deposit: {
                name: '',
                bank_info: '',
                amount: '',
                type: 'bank',
                currency: '',
                symbol: '',
                accept_terms: false
            },
        }
    },
    setup(props) {
        const router = useRouter();
        return {
            router
        };
    },
    computed: {},
    mounted() {
        window.scrollTo(0, 0);
    },

    methods: {
        setMinAmount: function () {
            this.withdraw.amount = this.setting.min_withdrawal;
        },
        setMaxAmount: function () {
            this.withdraw.amount = this.setting.max_withdrawal;
        },
        setPercentAmount: function (percent) {
            this.withdraw.amount = (percent / 100) * this.wallet.balance_withdrawal;
        },
        async getWallet() {
            const _toast = useToast();
            this.isLoading = true;

            try {
                // Primeiro, obtenha as informações da carteira
                const walletResponse = await HttpApi.get('profile/wallet');
                this.wallet = walletResponse.data.wallet;

                this.withdraw.currency = this.wallet.currency;
                this.withdraw.symbol = this.wallet.symbol;
                this.withdraw_deposit.currency = this.wallet.currency;
                this.withdraw_deposit.symbol = this.wallet.symbol;

                // Em seguida, obtenha as informações do usuário
                const userResponse = await HttpApi.get('profile/');
                console.log('User Response:', userResponse); // Verifique a resposta no console
                this.withdraw.pix_key = userResponse.data.user.cpf; // Preenchendo o campo pix_key

                this.isLoading = false;
            } catch (error) {
                const errorData = JSON.parse(error.request.responseText);
                Object.entries(errorData).forEach(([key, value]) => {
                    _toast.error(`${value}`);
                });
                this.isLoading = false;
            }
        },
        getSetting: function () {
            const _this = this;
            const settingStore = useSettingStore();
            const settingData = settingStore.setting;

            if (settingData) {
                _this.setting = settingData;
                _this.withdraw.amount = settingData.min_withdrawal;
                _this.withdraw_deposit.amount = settingData.min_withdrawal;
            }

            _this.isLoading = false;
        },
        submitWithdrawBank: function (event) {
            const _this = this;
            const _toast = useToast();
            _this.isLoading = true;

            HttpApi.post('wallet/withdraw/request', _this.withdraw_deposit).then(response => {
                _this.isLoading = false;
                _this.withdraw_deposit = {
                    name: '',
                    bank_info: '',
                    amount: '',
                    type: '',
                    accept_terms: false
                }

                _this.router.push({ name: 'profileTransactions' });
                _toast.success(response.data.message);
            }).catch(error => {
                const errorData = JSON.parse(error.request.responseText);
                Object.entries(errorData).forEach(([key, value]) => {
                    _toast.error(`${value}`);
                });
                _this.isLoading = false;
            });
        },
        submitWithdraw: function (event) {
            const _this = this;
            const _toast = useToast();
            _this.isLoading = true;

            HttpApi.post('wallet/withdraw/request', _this.withdraw).then(response => {
                _this.isLoading = false;
                _this.withdraw = {
                    name: '',
                    pix_key: '',
                    pix_type: '',
                    amount: '',
                    type: '',
                    accept_terms: false
                }

                _this.router.push({ name: 'profileTransactions' });
                _toast.success(response.data.message);
            }).catch(error => {
                const errorData = JSON.parse(error.request.responseText);
                Object.entries(errorData).forEach(([key, value]) => {
                    _toast.error(`${value}`);
                });
                _this.isLoading = false;
            });
        }
    },


    created() {
        this.getWallet();
        this.getSetting();


    },
    watch: {},
};
</script>

<style scoped></style>
