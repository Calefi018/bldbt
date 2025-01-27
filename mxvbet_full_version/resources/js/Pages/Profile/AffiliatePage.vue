<style>
    .teste-place {
        color: #999B9B;
    }
</style>
<template>
    <BaseLayout>
        <div class="container mx-auto p-4 mt-20 relative  min-h-[calc(100vh-565px)]" style="padding: 0 2%;">
            <div v-if="wallet && !isLoading" class="grid grid-cols-1 mx-auto w-full sm:max-w-[690px] lg:max-w-[710px] w-full">
                <div v-if="isShowForm" class="col-span-1 shadow-lg mb-3 p-4" style="background-color: var(--footer-color-dark);border-radius: 5px;">
                    
                    <div class="mt-3 p-4">
                        <div class="flex flex-col mb-4">
                            <h1 data-v-a6a3f6da="" class="user-page-title mb-3" style="color: var(--ci-primary-color);font-weight: bold;font-size: 1.5em;">Indique um amigo e ganhe dinheiro</h1>
                            <p data-v-a6a3f6da="" class="refers-text warning xl:text-sm mb-3" style="color: #FF9A40;font-size: 14px;font-weight: 600;">Ganhe muito dinheiro! receba % de todos depósitos que seus indicados depositarem na plataforma, e acompanhe seu progresso em tempo real. </p>
                            <div class="flex flex-col">
                            <label aria-readonly="false" style="font-weight: 600;opacity: .5;" for="reference-code" class="block text-sm font-medium text-gray-900 dark:text-white">{{ $t('Seu link:') }}</label>
                            <div class="relative w-full">
                                <input style="background-color: var(--input-primary);font-size: .775em;opacity: .5;" type="text"
                                       id="referenceLink"
                                       class="teste-place block p-3 w-full z-20 text-sm text-gray-900 border-gray-300 bg-gray-50 rounded-lg rounded-gray-100 focus:border-gray-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:border-gray-500"
                                       :placeholder="$t('Reference Link')"
                                       v-model="referencelink"
                                       required readonly>
                                <button style="background-color: var(--ci-primary-color);color: var(--title-color);font-weight: 600;font-size: 14px;border-radius: 3px;padding-bottom: 2px;" @click.prevent="copyLink" type="submit"
                                        class="w-full mt-2 mb-3">
                                    <i style="color: var(--title-color);font-size: 14px;" class="fa-duotone fa-copy text-2xl pr-1"></i> Copiar link
                                </button>
                            </div>
                        </div>
                            <label style="font-weight: 600;opacity: .5;" for="reference-code" class="block text-sm font-medium text-gray-900 dark:text-white">{{ $t('Seu Código de referência:') }}</label>
                            <div class="relative w-full">
                                <input style="background-color: var(--input-primary);font-size: .775em;opacity: .5;" type="text"
                                       id="referenceCode"
                                       class="teste-place mb-3 block p-3 w-full z-20 text-sm text-gray-900 border-gray-300 bg-gray-50 rounded-lg rounded-gray-100 focus:border-gray-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:border-gray-500"
                                       :placeholder="$t('Reference Code')"
                                       v-model="referencecode"
                                       required readonly>
                                       <button style="background-color: var(--ci-primary-color);color: var(--title-color);font-weight: 600;font-size: 14px;border-radius: 3px;padding-bottom: 2px;" @click.prevent="copyCode" type="submit"
                                        class="w-full mt-2 mb-3">
                                    <i style="color: var(--title-color);font-size: 14px;" class="fa-duotone fa-copy text-2xl pr-1"></i> Copiar link
                                </button>
                            </div>

                            <h1 data-v-a6a3f6da="" class="user-page-title mb-3" style="color: var(--ci-primary-color);font-weight: bold;font-size: 1.5em;">Estatísticas</h1>
                            <template v-if="parseFloat(userData.affiliate_cpa) > 0">
                                <label style="font-weight: 600;opacity: .5;" for="reference-code" class="block text-sm font-medium text-gray-900 dark:text-white">
                                    {{ $t('CPA (R$)') }}
                                </label>
                                <div class="relative w-full">
                                    <input 
                                        style="background-color: var(--input-primary);font-size: .775em" 
                                        type="text"
                                        class="mb-3 block p-3 w-full z-20 text-sm text-gray-900 border-gray-300 bg-gray-50 rounded-lg rounded-gray-100 focus:border-gray-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:border-gray-500"
                                        :placeholder="state.currencyFormat(parseFloat(userData.affiliate_cpa), wallet.currency)"
                                        required 
                                        readonly
                                    >
                                </div>
                            </template>

                            <label style="font-weight: 600;opacity: .5;" for="reference-code" class="block text-sm font-medium text-gray-900 dark:text-white">{{ $t('RevShare (%)') }}</label>
                            <div class="relative w-full">
                                <input style="background-color: var(--input-primary);font-size: .775em" type="text"
                                       class="mb-3 block p-3 w-full z-20 text-sm text-gray-900 border-gray-300 bg-gray-50 rounded-lg rounded-gray-100 focus:border-gray-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:border-gray-500"
                                       :placeholder=" userData.affiliate_revenue_share_fake ? userData.affiliate_revenue_share_fake : userData.affiliate_revenue_share "
                                       required readonly>
                                    
                            </div>

                            <label style="font-weight: 600;opacity: .5;" for="reference-code" class="block text-sm font-medium text-gray-900 dark:text-white">{{ $t('Pessoas que você indicou') }}</label>
                            <div class="relative w-full">
                                <input style="background-color: var(--input-primary);font-size: .775em" type="text"
                                       class="mb-3 block p-3 w-full z-20 text-sm text-gray-900 border-gray-300 bg-gray-50 rounded-lg rounded-gray-100 focus:border-gray-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:border-gray-500"
                                       :placeholder=" indications  "
                                       required readonly>
                                    
                            </div>

                            <label style="font-weight: 600;opacity: .5;" for="reference-code" class="block text-sm font-medium text-gray-900 dark:text-white">{{ $t('Valor disponível') }}</label>
                            <div class="relative w-full">
                                <input style="background-color: var(--input-primary);font-size: .775em" type="text"
                                       class="mb-3 block p-3 w-full z-20 text-sm text-gray-90 rounded-lg rounded-gray-100 dark:bg-gray-700 dark:placeholder-gray-400 dark:text-white"
                                       :placeholder="  state.currencyFormat(parseFloat(wallet.refer_rewards), wallet.currency)   "
                                       required readonly>
                                    
                            </div>

                            <button @click.prevent="opemModalWithdrawal" type="button" class="ui-button-blue w-full flex justify-center items-center" style="font-size: 14px;font-weight: 600;">
                                <i style="font-size: 14px;font-weight: 600;" class="fa-light fa-envelope-open-dollar pr-1"></i> <p style="font-size: 14px;font-weight: 600;"> Solicitar saque</p>  
                            </button>
                        </div>

                       

                        <div class="mt-16 grid grid-cols-1 md:grid-cols-1 gap-4">
                            <!-- <button @click.prevent="generateCode" type="button" class="ui-button-yellow">
                                {{ $t('Create another code') }}
                            </button> -->
                            <p style="font-size: 12px;opacity: .7;padding: 20px;margin-top:-30px;text-align: center;">Nossa plataforma dispõe de um painel de afiliados avançado, permitindo que você visualize detalhes sobre ganhos e perdas. Além disso, oferece a capacidade de adicionar subafiliados.</p>
                            <button type="button" class="ui-button-blue" style="max-width: 350px;border-radius: 8px;margin: 0 auto;padding: 10px 40px;margin-bottom: 30px">
                                <a href="/affiliate/login" target="_blank">Painel do Afiliado</a>
                                <!-- {{ $t('Share on social media') }} -->
                            </button>
                        </div>

                        <!-- <div class="mt-5 flex justify-end items-end">
                            <button @click="$router.push('/terms-conditions/reference')" type="button" class="text-gray-500 hover:text-gray-600 dark:text-gray-300 hover:dark:text-gray-400">
                                {{ $t('Terms and Conditions of Reference') }} <i class="fa-regular fa-arrow-right ml-2"></i>
                            </button>
                        </div> -->
                    </div>
                </div>
                <div v-else class="relative flex flex-col items-center justify-center text-center p-6">
                    <div v-if="!isLoadingGenerate" class="">
                        <p class="text-gray-400">
                            {{ $t('Se torne agora mesmo um Afiliado da casa e lucre até R$20000 por dia apenas indicando pessoas, acompanhe seus ganhos em tempo real!') }}
                        </p>
                        <div class="mt-5 w-full">
                            <button @click.prevent="generateCode" type="button" class="ui-button-blue w-full" style="font-weight: bold;color: var(--title-color);">
                                {{ $t('Tornar-me um Afiliado') }}
                            </button>
                        </div>
                    </div>

                    <div v-if="isLoadingGenerate" role="status" class="absolute -translate-x-1/2 -translate-y-1/2 top-2/4 left-1/2">
                        <i class="fa-duotone fa-spinner-third fa-spin" style="font-size: 45px;--fa-primary-color: var(--ci-primary-color); --fa-secondary-color: #000000;"></i>
                        <span class="sr-only">{{ $t('Loading') }}...</span>
                    </div>
                </div>
              
            </div>
            <div v-else role="status" class="absolute -translate-x-1/2 -translate-y-1/2 top-2/4 left-1/2 h-full mt-16">
                <div class="text-center flex flex-col justify-center items-center">
                    <i class="fa-duotone fa-spinner-third fa-spin" style="font-size: 45px;--fa-primary-color: var(--ci-primary-color); --fa-secondary-color: #000000;"></i>
                    <span class="mt-3">{{ $t('Loading') }}...</span>
                </div>
            </div>
        </div>

        <!-- MODAL RECOMPENSAS DE REFERÊNCIA -->
        <div id="referenceRewardsEl" tabindex="-1" aria-hidden="true" class="fixed left-0 right-0 top-0 z-50 hidden h-[calc(100%-1rem)] max-h-full w-full overflow-y-auto overflow-x-hidden p-4 md:inset-0">
            <div class="relative max-h-full w-full max-w-2xl">
                <!-- Modal content -->
                <div class="relative rounded-lg bg-white shadow dark:bg-gray-700">

                    <!-- Modal header -->
                    <div class="flex justify-between p-4 dark:bg-gray-600 rounded-t-lg">
                        <h1>{{ $t('Referral Reward Rules') }}</h1>
                        <button class="" @click.prevent="toggleReferenceRewards">
                            <i class="fa-solid fa-xmark"></i>
                        </button>
                    </div>

                    <!-- Modal body -->
                    <div class="w-full flex justify-center p-4">
                        <div class="flex items-center">
                            <div class="l"></div>
                            <div class="text-white px-3">
                                Regras de Desbloqueio
                            </div>
                            <div class="r"></div>
                        </div>


                    </div>
                </div>
            </div>
        </div>

        <!-- MODAL RECOMPENSAS POR COMISSÃO -->
        <div id="commissionRewardsEl" tabindex="-1" aria-hidden="true" class="fixed left-0 right-0 top-0 z-50 hidden h-[calc(100%-1rem)] max-h-full w-full overflow-y-auto overflow-x-hidden p-4 md:inset-0">
            <div class="relative max-h-full w-full max-w-2xl">
                <!-- Modal content -->
                <div class="relative rounded-lg bg-white shadow dark:bg-gray-700">

                    <!-- Modal header -->
                    <div class="flex justify-between p-4 dark:bg-gray-600 rounded-t-lg">
                        <h1>Regras de recompensas por comissão</h1>
                        <button class="" @click.prevent="toggleCommissionRewards">
                            <i class="fa-solid fa-xmark"></i>
                        </button>
                    </div>

                    <!-- Modal body -->
                    <div class="flex flex-col  w-full justify-center p-4">
                        <div class="flex items-center text-center w-full justify-center">
                            <div class="l"></div>
                            <div class="text-white px-3">
                                Taxas de comissões
                            </div>
                            <div class="r"></div>
                        </div>

                        <div class="mt-5">
                            <ul>
                                <li class="flex dark:bg-gray-800 shadow rounded-lg aposta-1 w-full p-4 mb-3">
                                    <div>
                                        <h1 class="font-mono text-4xl font-bold">7%</h1>
                                        <p class="text-gray-400 text-sm"><strong class="text-gray-400">Jogo:</strong> Os Jogos Originais</p>
                                    </div>
                                </li>
                                <li class="flex dark:bg-gray-800 shadow rounded-lg aposta-2 w-full p-4 mb-3">
                                    <div>
                                        <h1 class="font-mono text-4xl font-bold">7%</h1>
                                        <p class="text-gray-400 text-sm"><strong class="text-gray-400">Jogo:</strong> slots de terceiros, cassino ao vivo</p>
                                    </div>
                                </li>
                                <li class="flex dark:bg-gray-800 shadow rounded-lg aposta-3 w-full p-4 mb-3">
                                    <div>
                                        <h1 class="font-mono text-4xl font-bold">25%</h1>
                                        <p class="text-gray-400 text-sm"><strong class="text-gray-400">Jogo:</strong> Esportes</p>
                                    </div>
                                </li>
                            </ul>
                        </div>

                        <div class="mt-5 ml-4">
                            <ul class="list-outside list-disc">
                                <li class="mb-3">
                                    Em qualquer ambiente público (por exemplo, universidades, escolas, bibliotecas e espaços de escritório), apenas uma comissão pode ser paga para cada usuário,
                                    endereço IP, dispositivo eletrônico, residência, número de telefone, método de cobrança, endereço de e-mail e computador e IP endereço compartilhado com outras pessoas.
                                </li>
                                <li class="mb-3">
                                    Nossa decisão de fazer uma aposta será baseada inteiramente em nosso critério depois que um depósito for feito e uma aposta for feita com sucesso.
                                </li>
                                <li class="mb-3">
                                    As comissões podem ser retiradas em nossa carteira CREDK interna do painel a qualquer momento. (Veja a extração de sua comissão no painel e visualize o saldo na carteira).
                                </li>
                                <li class="mb-3">
                                    Apoiamos a maioria das moedas no mercado.
                                </li>
                                <li class="mb-3">
                                    O sistema calcula a comissão a cada 24 horas.
                                </li>
                            </ul>
                        </div>

                        <div class="mt-5 w-full border dark:border-gray-500 p-4 rounded">
                            Se você tiver alguma dúvida sobre nossas regras, por favor <a href="" class="text-green-500 font-bold"> Contate-nos </a>
                        </div>

                    </div>
                </div>
            </div>
        </div>

        <!-- MODAL SAQUE -->
        <div id="withdrawalEl" tabindex="-1" aria-hidden="true" class="fixed left-0 right-0 top-0 z-50 hidden h-[calc(100%-1rem)] max-h-full w-full overflow-y-auto overflow-x-hidden p-4 md:inset-0">
            <div class="relative max-h-full w-full max-w-2xl">
                <!-- Modal content -->
                <div class="relative rounded-lg bg-white shadow dark:bg-gray-700">

                    <!-- Modal header -->
                    <div class="flex justify-between p-4 dark:bg-gray-600 rounded-t-lg">
                        <h1>Regras de recompensas por comissão</h1>
                        <button class="" @click.prevent="opemModalWithdrawal">
                            <i class="fa-solid fa-xmark"></i>
                        </button>
                    </div>

                    <!-- Modal body -->
                    <div class="flex flex-col  w-full justify-center p-4">
                        <form action="" @submit.prevent="makeWithdrawal">
                            <div class="dark:text-gray-400 mb-3">
                                <label for="">Valor do Saque</label>
                                <input v-model="withdrawalForm.amount" type="number" class="input" placeholder="Valor do saque" required>
                                <span v-if="wallet" class="text-sm italic">Saldo: {{ state.currencyFormat(parseFloat(wallet?.refer_rewards), wallet?.currency) }}</span>
                            </div>

                            <div class="dark:text-gray-400 mb-3">
                                <label for="">Chave Pix (CPF)</label>
                                <input v-model="withdrawalForm.pix_key"  
                                   v-maska
                                   data-maska="[
                                    '###.###.###-##',
                                    '##.###.###/####-##'
                                   ]" type="text" class="input" placeholder="Digite a sua Chave pix" required>
                            </div>

                            <!-- <div class="dark:text-gray-400 mb-3">
                                    <label for="">Tipo de Chave</label>
                                    <select v-model="withdraw.pix_type" name="type_document" class="input" required>
                                        <option value="document">CPF/CNPJ</option>
                                    </select>
                                </div> -->

                            <button type="submit" class="mt-5 w-full bg-green-800 text-white hover:bg-green-600 px-4 py-2 transition duration-700">
                                Solicitar agora <i class="fa-regular fa-arrow-right ml-2"></i>
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </div>

    </BaseLayout>
</template>


<script>

import BaseLayout from "@/Layouts/BaseLayout.vue";
import { Modal } from 'flowbite';
import HttpApi from "@/Services/HttpApi.js";
import {useToast} from "vue-toastification";
import {useAuthStore} from "@/Stores/Auth.js";
import {useRouter} from "vue-router";

export default {
    props: [],
    components: { BaseLayout, Modal },
    data() {
        return {
            isLoading: false,
            referenceRewards: null,
            commissionRewards: null,
            isShowForm: false,
            isLoadingGenerate: false,
            code: '',
            urlCode: '',
            referencecode: '',
            referencelink: '',
            wallet: null,
            indications: 0,
            histories: null,
            withdrawalModal: null,
            withdrawalForm: {
                amount: 0,
                pix_key: '',
                pix_type: 'document',
            }
        }
    },
    setup(props) {
        const router = useRouter();
        return {
            router
        };
    },
    computed: {
        userData() {
            const authStore = useAuthStore();
            return authStore.user;
        }
    },
    mounted() {
        window.scrollTo(0, 0);
        this.referenceRewards = new Modal(document.getElementById('referenceRewardsEl'), {
            placement: 'center',
            backdrop: 'dynamic',
            backdropClasses: 'bg-gray-900/50 dark:bg-gray-900/80 fixed inset-0 z-40',
            closable: true,
            onHide: () => {

            },
            onShow: () => {

            },
            onToggle: () => {

            },
        });

        this.commissionRewards = new Modal(document.getElementById('commissionRewardsEl'), {
            placement: 'center',
            backdrop: 'dynamic',
            backdropClasses: 'bg-gray-900/50 dark:bg-gray-900/80 fixed inset-0 z-40',
            closable: true,
            onHide: () => {

            },
            onShow: () => {

            },
            onToggle: () => {

            },
        });

        this.withdrawalModal = new Modal(document.getElementById('withdrawalEl'), {
            placement: 'center',
            backdrop: 'dynamic',
            backdropClasses: 'bg-gray-900/50 dark:bg-gray-900/80 fixed inset-0 z-40',
            closable: false,
            onHide: () => {

            },
            onShow: () => {

            },
            onToggle: () => {

            },
        });
    },
    methods: {
        copyCode: function(event) {
            const _toast = useToast();
            var inputElement = document.getElementById("referenceCode");
            inputElement.select();
            inputElement.setSelectionRange(0, 99999);  // Para dispositivos móveis

            // Copia o conteúdo para a área de transferência
            document.execCommand("copy");
            _toast.success(this.$t('Code copied successfully'));
        },
        copyLink: function(event) {
            const _toast = useToast();
            var inputElement = document.getElementById("referenceLink");
            inputElement.select();
            inputElement.setSelectionRange(0, 99999);  // Para dispositivos móveis

            // Copia o conteúdo para a área de transferência
            document.execCommand("copy");
            _toast.success(this.$t('Link copied successfully'));
        },
        getCode: function() {
            const _this = this;
            const _toast = useToast();
            _this.isLoadingGenerate = true;

            HttpApi.get('profile/affiliates/')
                .then(response => {
                    if( response.data.code !== '' && response.data.code !== undefined && response.data.code !== null) {
                        _this.isShowForm = true;
                        _this.code          = response.data.code;
                        _this.referencecode = response.data.code;
                        _this.urlCode       = response.data.url;
                    }

                    _this.indications   = response.data.indications;
                    _this.referencelink = response.data.url;
                    _this.wallet        = response.data.wallet;
                    _this.withdrawalForm.amount = response.data.wallet.refer_rewards;

                    _this.isLoadingGenerate = false;
                })
                .catch(error => {
                    _this.isShowForm = false;
                    _this.isLoadingGenerate = false;
                });
        },
        generateCode: function(event) {
            const _this = this;
            const _toast = useToast();
            _this.isLoadingGenerate = true;

            HttpApi.get('profile/affiliates/generate')
                .then(response => {
                    if(response.data.status) {
                        _this.getCode();
                        _toast.success(_this.$t('Your code was generated successfully'));
                    }

                    _this.isLoadingGenerate = false;
                })
                .catch(error => {
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {
                        _toast.error(`${value}`);
                    });
                    _this.isLoadingGenerate = false;
                });
        },
        toggleCommissionRewards: function(event) {
            this.commissionRewards.toggle();
        },
        toggleReferenceRewards: function(event) {
            this.referenceRewards.toggle();
        },
        opemModalWithdrawal: function() {
            this.withdrawalModal.toggle();
        },
        makeWithdrawal: async function() {
            const _this = this;
            const _toast = useToast();

            _this.isLoading = true;

            HttpApi.post('profile/affiliates/request', _this.withdrawalForm)
                .then(response => {
                    _this.opemModalWithdrawal();

                    _toast.success(_this.$t(response.data.message));
                    _this.isLoading = false;
                    _this.router.push({ name: 'profileWallet' });
                })
                .catch(error => {
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {
                        _toast.error(`${value}`);
                    });
                    _this.isLoading = false;
                });
        }
    },
    created() {
      this.getCode();
    },
    watch: {

    },
};
</script>

<style scoped>

</style>
