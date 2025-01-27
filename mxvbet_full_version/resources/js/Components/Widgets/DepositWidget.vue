<template>

        <div v-if="(paymentType == null || paymentType === '') && wallet && setting">
            <div class="w-full">
                <ul>
                    <li v-if="setting.suitpay_is_enable" @click="setPaymentMethod('pix', 'ibpay')" class="rounded mx-auto cursor-pointer flex justify-between hover:bg-green-700/20 px-4 py-3 mb-3 bg-gray-200 dark:bg-gray-800/50 hover:dark:bg-gray-900">
                        <div class="flex items-center gap-4">
                            <img :src="`/assets/images/pix.png`" alt="" width="100">
                            <p>Pagamento PIX</p>
                        </div>
                        <div class="flex justify-center items-center text-gray-500 gap-4">
                            <i class="fa-solid fa-chevron-right ml-2"></i>
                        </div>
                    </li>
                </ul>
            </div>
        </div>
    
        <div v-if="setting && paymentType === 'pix' && (setting.suitpay_is_enable)">
            <div v-if="showPixQRCode && wallet" class="w-full">
                <div class="w-full p-4 bg-white dark:bg-gray-700 rounded mb-3"style="background-color: var(--navtop-color-dark);">
                    <div class="flex justify-between">
                        <h2 class="text-lg">Falta pouco! Escaneie o código QR pelo seu app de pagamentos ou Internet Banking</h2>
                        <div class="text-4xl">
                            <i class="fa-regular fa-circle-dollar"></i>
                        </div>
                    </div>
                </div>
    
                <div class="w-full p-4">
                    <div>
                        <p class="font-bold">Valor do Pix a pagar: {{ state.currencyFormat(parseFloat(deposit.amount), wallet.currency) }}</p>
                    </div>
                    <div class="p-3 flex justify-center items-center">
                        <QRCodeVue3 :value="qrcodecopypast"/>
                    </div>
                    <div>
                        <p class="font-bold">Código válido por 23 horas.</p>
                    </div>
                    <div class="mt-4">
                        <p class="mb-3">Se preferir, você pode pagá-lo copiando e colando o código abaixo:</p>
                        <input id="pixcopiaecola" type="text" class="input" v-model="qrcodecopypast">
                    </div>
    
                    <div class="mt-5 w-full flex items-center justify-center">
                        <button @click.prevent="copyQRCode" type="button" class="ui-button-blue w-full">
                            <span class="uppercase font-semibold text-sm">{{ $t('Copy code') }}</span>
                        </button>
                    </div>
                </div>
            </div>
            <div v-if="!showPixQRCode">
                <div v-if="setting != null && wallet != null && isLoading === false" class="w-full">
                    <form action="" @submit.prevent="submitQRCode">
                        <div class="flex items-center justify-between">
                            <p class="text-gray-500">{{ $t('Deposit Currency') }}</p>
                            <button type="button" class="flex justify-center items-center mr-3 pt-1">
                                <div>{{ wallet.currency }}</div>
                                <div class="mr-2 ml-2">
                                    <img :src="`/assets/images/coin/BRL.png`" alt="" width="32">
                                </div>
                                <div class="ml-2 text-sm">
                                    <i class="fa-solid fa-chevron-down"></i>
                                </div>
                            </button>
                        </div>
                        <img :src="`/assets/images/pix.png`" alt="" width="100">
    
                        <div class="mt-5">
                            <input type="text"
                                   v-model="deposit.cpf"
                                   v-maska
                                   data-maska="[ '###.###.###-##' ]"
                                   class="mt-2 border-none text-gray-600 placeholder:text-gray-300 dark:text-gray-200 dark:placeholder:text-gray-500 w-full bg-white dark:bg-gray-900 font-sans transition-all duration-300 disabled:cursor-not-allowed disabled:opacity-75 px-2 text-sm leading-5 rounded py-3"
                                   placeholder="Digite o CPF"
                                   required>
                        </div>
    
                        <div class="mt-3">
                            <div class="w-full flex items-center justify-between bg-white dark:bg-gray-900 rounded py-1">
                                <div class="flex w-full">
                                    <input type="text"
                                           v-model="deposit.amount"
                                           class="appearance-none border border-gray-300 rounded-md bg-transparent border-none w-full"
                                           :min="setting.min_deposit"
                                           :max="setting.max_deposit"
                                           :placeholder="$t('Enter the value here')"
                                           required
                                    >
                                </div>
                            </div>
    
                            <div class="item-selected">
                                <div
                                    @click.prevent="setAmount(parseFloat(setting.min_deposit))"
                                    class="item rounded"
                                    :class="{'active': selectedAmount === parseFloat(setting.min_deposit)}"
                                >
                                    <button type="button">
                                        {{ state.currencyFormat(parseFloat(setting.min_deposit), wallet.currency) }}
                                    </button>
                                    <div v-if="selectedAmount === parseFloat(setting.min_deposit)" class="ratio">
                                        +{{ setting.initial_bonus }}%
                                    </div>
                                    <img v-if="selectedAmount === parseFloat(setting.min_deposit)" class="img-check" :src="`/assets/images/check.webp`" alt="">
                                </div>
                                <div
                                    @click.prevent="setAmount(25.00)"
                                    class="item rounded"
                                    :class="{'active': selectedAmount === 25.00}"
                                >
                                    <button type="button">{{ wallet.symbol }} 25,00</button>
                                    <div v-if="selectedAmount === 25.00" class="ratio">+{{ setting.initial_bonus }}%</div>
                                    <img v-if="selectedAmount === 25.00" class="img-check" :src="`/assets/images/check.webp`" alt=""/>
                                </div>
    
                                <div
                                    @click.prevent="setAmount(50.00)"
                                    class="item rounded"
                                    :class="{'active': selectedAmount === 50.00}"
                                >
                                    <button type="button">{{ wallet.symbol }} 50,00</button>
                                    <div v-if="selectedAmount === 50.00" class="ratio">+{{ setting.initial_bonus }}%</div>
                                    <img v-if="selectedAmount === 50.00" class="img-check" :src="`/assets/images/check.webp`" alt=""/>
                                </div>
                            </div>
                        </div>
    
                        <div class="mt-3 text-gray-500 flex flex-col items-center">
                            <p class="text-center">
                                {{ $t('Get an extra bonus') }} 
                                <strong class="text-white font-bold">{{ setting.initial_bonus }}%</strong> 
                                {{ $t('on a minimum deposit of') }} 
                                <strong class="text-white font-bold">{{ state.currencyFormat(parseFloat(setting.min_deposit), wallet.currency) }}</strong>
                            </p>
                        </div>
    
                        <div class="flex justify-center mt-3">
                            <label class="inline-flex items-center cursor-pointer">
                                <input type="checkbox" v-model="deposit.accept_bonus" class="sr-only peer">
                                <div class="relative w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-green-300 dark:peer-focus:ring-green-800 rounded-full peer dark:bg-gray-700 peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:rounded-full after:w-5 after:h-5 after:transition-all dark:border-gray-600 peer-checked:bg-green-600"></div>
                                <span class="ms-3 text-sm font-medium text-gray-900 dark:text-gray-300">Aceitar Bônus</span>
                            </label>
                        </div>
    
                        <div class="mt-5 w-full flex items-center justify-center">
                            <button type="submit" class="ui-button-blue w-full">
                                <span class="uppercase font-semibold text-sm">{{ $t('Deposit') }}</span>
                            </button>
                        </div>
                    </form>
    
                </div>
    
                <div v-if="isLoading" role="status" class="absolute -translate-x-1/2 -translate-y-1/2 top-2/4 left-1/2">
                    <svg aria-hidden="true" class="w-8 h-8 text-gray-200 animate-spin dark:text-gray-600 fill-green-600" viewBox="0 0 100 101" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" preserveaspectratio="xMidYMid meet" style="animation: rotate 1s linear infinite;">
                        <circle cx="50" cy="50" r="45" stroke="currentColor" stroke-width="10" fill="none"></circle>
                        <circle cx="50" cy="50" r="45" stroke="currentColor" stroke-width="6" fill="none" stroke-linecap="round" stroke-dasharray="283 100" stroke-dashoffset="280" style="animation: dash 1.5s ease-in-out infinite;"></circle>
                    </svg>
                </div>
            </div>
        </div>

    
</template>

<script>
    import {useToast} from "vue-toastification";
    import HttpApi from "@/Services/HttpApi.js";
    import QRCodeVue3 from "qrcode-vue3";
    import {useAuthStore} from "@/Stores/Auth.js";
    import { StripeCheckout } from '@vue-stripe/vue-stripe';
    import {useSettingStore} from "@/Stores/SettingStore.js";

    export default {
        props: ['showMobile', 'title', 'isFull'],
        components: { QRCodeVue3, StripeCheckout },
        data() {

            return {
                isLoading: false,
                minutes: 15,
                seconds: 0,
                timer: null,
                setting: null,
                wallet: null,
                deposit: {
                    amount: '',
                    cpf: '',
                    gateway: '',
                    accept_bonus: false
                },
                selectedAmount: 0,
                showPixQRCode: false,
                qrcodecopypast: '',
                idTransaction: '',
                intervalId: null,

                /// stripe
                elementsOptions: {
                    appearance: {}, // appearance options
                },
                confirmParams: {
                    return_url: null, // success url
                },
                successURL: null,
                cancelURL: null,
                amount: null,
                currency: null,
                publishableKey: null,
                sessionId: null,

                paymentType: 'pix',
                paymentGateway: 'ibpay'
            }
        },
        setup(props) {


            return {};
        },
        computed: {
            isAuthenticated() {
                const authStore = useAuthStore();
                return authStore.isAuth;
            },
        },
        mounted() {
            this.modalDeposit = new Modal(document.getElementById('modalElDeposit'), {
                placement: 'center',
                backdrop: 'dynamic',
                backdropClasses: 'bg-gray-900/50 dark:bg-gray-900/80 fixed inset-0 z-40',
                closable: true,
                onHide: () => {
                    this.paymentType = null;
                },
                onShow: () => {

                },
                onToggle: () => {

                },
            });
        },
        beforeUnmount() {
            clearInterval(this.timer);
            this.paymentType = null;
        },
        methods: {
            toggleBonus() {
                this.deposit.accept_bonus = !this.deposit.accept_bonus;
                if (this.deposit.accept_bonus) {
                    console.log("Bônus aceito.");
                    // Lógica adicional quando o bônus é aceito, como enviar uma requisição
                } else {
                    console.log("Bônus recusado.");
                    // Lógica adicional quando o bônus é recusado
                }
            },
            getSession: function() {
                const _this = this;
                HttpApi.post('stripe/session', { amount: _this.amount, currency: _this.currency}).then(response => {
                    if(response.data.id) {
                        _this.sessionId = response.data.id;
                    }
                }).catch(error => { });
            },
            checkoutStripe: function() {
                const _toast = useToast();
                if(this.amount <= 0 || this.amount === '') {
                    _toast.error('Você precisa digitar um valor');
                    return;
                }

                this.$refs.checkoutRef.redirectToCheckout();
            },
            getPublicKeyStripe: function() {
                const _this = this;
                HttpApi.post('stripe/publickey', {}).then(response => {
                    _this.$nextTick(() => {
                        _this.publishableKey = response.data.stripe_public_key;
                        _this.elementsOptions.clientSecret  = response.data.stripe_secret_key;
                        _this.confirmParams.return_url      = response.data.successURL;
                    });

                }).catch(error => { });
            },
            setPaymentMethod: function(type, gateway) {
                this.paymentType = type;
                this.paymentGateway = gateway;
            },
            openModalDeposit: function() {
                this.modalDeposit.toggle();
            },
            submitQRCode: function(event) {
                const _this = this;
                const _toast = useToast();

                if (_this.deposit.cpf === '') {
                    _toast.error(_this.$t('You need to enter a CPF'));
                    return;
                }

                if(_this.deposit.amount === '' || _this.deposit.amount === undefined) {
                    _toast.error(_this.$t('You need to enter a value'));
                    return;
                }

                if(_this.deposit.cpf === '' || _this.deposit.cpf === undefined) {
                    _toast.error(_this.$t('Do you need to enter your CPF or CNPJ'));
                    return;
                }

                if(parseFloat(_this.deposit.amount) < parseFloat(_this.setting.min_deposit)) {
                    _toast.error('O valor mínimo de depósito é de '+ _this.setting.min_deposit);
                    return;
                }

                if(parseFloat(_this.deposit.amount) < 5) {
                    _toast.error('O valor mínimo de depósito é de '+ 'R$5.00');
                    return;
                }

                if(parseFloat(_this.deposit.amount) > parseFloat(_this.setting.max_deposit)) {
                    _toast.error('O valor máximo de depósito é de '+ _this.setting.min_deposit);
                    return;
                }

                _this.deposit.paymentType = _this.paymentType;
                _this.deposit.gateway = 'ibpay';

                _this.isLoading = true;
                HttpApi.post('wallet/deposit/payment', _this.deposit)
                    .then(response => {
                        if (response.data && response.data.idTransaction && response.data.qrcode) {
                            // Quando a resposta contém os dados esperados
                            _this.showPixQRCode = true;
                            _this.idTransaction = response.data.idTransaction;
                            _this.qrcodecopypast = response.data.qrcode;
                            _this.isLoading = false;
                        } else {
                            // Caso a resposta não contenha os dados esperados
                            _toast.error('Dados inválidos.');
                            _this.showPixQRCode = false;
                            _this.isLoading = false;
                        }
                    })
                    .catch(error => {
                        // Verifica se a resposta do erro tem o formato esperado
                        try {
                            const errors = JSON.parse(error.request.responseText);
                            Object.entries(errors).forEach(([key, value]) => {
                                _toast.error(`${value}`);
                            });
                        } catch (parseError) {
                            // Caso não seja possível parsear a resposta do erro
                            _toast.error('Erro inesperado. Tente novamente mais tarde.');
                        }
                        
                        _this.showPixQRCode = false;
                        _this.isLoading = false;
                    });
            },
            copyQRCode: function(event) {
                const _toast = useToast();
                var inputElement = document.getElementById("pixcopiaecola");
                inputElement.select();
                inputElement.setSelectionRange(0, 99999);  // Para dispositivos móveis

                // Copia o conteúdo para a área de transferência
                document.execCommand("copy");
                _toast.success('Pix Copiado com sucesso');
            },
            setAmount: function(amount) {
                this.deposit.amount = amount;
                this.selectedAmount = amount;
            },
            getWallet: function() {
                const _this = this;
                const _toast = useToast();
                _this.isLoadingWallet = true;

                HttpApi.get('profile/wallet')
                    .then(response => {
                        _this.wallet = response.data.wallet;
                        _this.currency = response.data.wallet.currency;
                        _this.isLoadingWallet = false;
                    })
                    .catch(error => {
                        const _this = this;
                        Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {
                            _toast.error(`${value}`);
                        });
                        _this.isLoadingWallet = false;
                    });
            },
            getSetting: function() {
                const _this = this;
                const settingStore = useSettingStore();
                const settingData = settingStore.setting;

                if(settingData) {
                    _this.setting = settingData;
                    _this.amount  = settingData.max_deposit;

                    if(_this.paymentType === 'stripe' && settingData.stripe_is_enable) {
                        _this.getSession();
                    }
                }
            },
        },
        created() {
            if(this.isAuthenticated) {
                this.getWallet();
                this.getSetting();

                if(this.paymentType === 'stripe') {
                    this.getSession();
                    this.currency = 'USD';
                }
            }
        },
        watch: {
            amount(oldValue, newValue) {
                if(this.paymentType === 'stripe') {
                    this.getSession();
                    this.currency = 'USD';
                }

            },
            currency(oldValue, newValue) {
                if(this.paymentType === 'stripe') {
                    this.getSession();
                }
            }
        },
    };
</script>

<style scoped>

.item-selected {
    display: flex;
    gap: 10px; /* Espaçamento entre os itens */
    justify-content: space-between; /* Distribui o espaço uniformemente */
    align-items: center; /* Alinha os itens verticalmente no centro */
    padding: 10px;
}

.item {
    flex: 1; /* Faz cada item ocupar o mesmo espaço */
    text-align: center;
}

.item button {
    width: 100%; /* Garante que o botão ocupe todo o espaço do item */
    padding: 10px;
}

.item .ratio {
    margin-top: 5px;
    font-size: 0.9rem;
}

.item .img-check {
    margin-top: 5px;
    width: 20px;
    height: 20px;
}

</style>
