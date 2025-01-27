<style>
.rounded-button {
  width: 100px; /* Ajuste conforme necessário */
  height: 50px; /* Ajuste conforme necessário */
  border-radius: 2px; /* Faz o botão arredondado */
  border: 1px solid #ccc; /* Ajuste a cor da borda conforme necessário */
  background-color: #007bff; /* Ajuste a cor de fundo conforme necessário */
  color: white; /* Ajuste a cor do texto conforme necessário */
  font-size: 16px; /* Ajuste o tamanho da fonte conforme necessário */
  cursor: pointer;
}

.container-deposit {
    margin: 4%;
}
.ui-button-blue2 {
    font-size: .875rem; /* Define o tamanho da fonte como 0.875 rem (em torno de 14px). */
    font-weight: 700;   /* Define o peso da fonte como 700, que é negrito. */
    line-height: 1.25rem; /* Define a altura da linha como 1.25 rem (em torno de 20px), o que melhora a legibilidade do texto. */
    border-radius: 5px; /* Arredonda os cantos do botão com um raio de 26 pixels, fazendo com que o botão tenha bordas bem arredondadas. */
    
    /* Sombra do botão: aplica um efeito de sombra em diferentes navegadores */
    -webkit-box-shadow: 0px 2px 11px 0px var(--ci-primary-color); /* Sombra para navegadores WebKit, como o Chrome. */
    -moz-box-shadow: 0px 2px 11px 0px var(--ci-primary-color); /* Sombra para navegadores Firefox. */
    box-shadow: 0px 2px 11px 0px var(--ci-primary-color); /* Sombra padrão para todos os navegadores. */
    
    background-color: var(--ci-primary-color); /* Define a cor de fundo do botão usando uma variável CSS para a cor primária. */
    color: var(--title-color); /* Define a cor do texto do botão usando uma variável CSS para a cor do título. */
    
    width: auto; /* Define a largura do botão como automática, ajustando-se ao conteúdo do botão. */
    padding: 7px 15px; /* Adiciona preenchimento interno ao botão, com 9px de margem superior e inferior e 15px nas laterais. */
    
    /* Configurações de flexbox para que o botão não se ajuste ao layout flexível pai */
    -webkit-flex: none; /* Define o comportamento do botão no layout flexível para não crescer ou encolher, para navegadores WebKit. */
    -ms-flex: none; /* Define o comportamento do botão no layout flexível para não crescer ou encolher, para navegadores com suporte a Flexbox no IE. */
    flex: none; /* Define o comportamento do botão no layout flexível para não crescer ou encolher, para navegadores modernos. */
}


.ui-button-blue2:hover {
    opacity: .9;
}

@media(max-width:768px) {
    .container-deposit {
        margin: 0;
        width: 100vw;
        height: 100vh;
    }
    .ui-button-blue2 {
    font-size: .775rem;
    font-weight: 700;
    line-height: 1.25rem;
    
    padding: 5px 8px;
   
}
}

</style>
<template>
    
    <button class="ui-button-blue2" id="animar-dep" @click.prevent="toggleModalDeposit" type="button" :class="[showMobile === true ? 'hidden md:block' : '', isFull ? 'w-full' : '']">
        {{ title }}
    </button>

    <div style="  background-color:rgba(0, 0, 0, 0.47); backdrop-filter: none;height: 100vh;" id="modalElDeposit" tabindex="-1" aria-hidden="true" class="fixed  top-0 left-0 right-0 z-1 hidden w-full overflow-x-hidden overflow-y-auto md:inset-0 h-screen md:h-[calc(100%-1rem)] max-h-full">
 
        <div class="relative w-full max-w-2xl max-h-full container-deposit" style="background-color: #212425;border-radius: 1px; max-width: 450px;margin: 0 auto;">

            
            
            <div class="flex flex-col px-6 pb-8 my-auto relative" style="justify-content: flex-end;position: relative;">

                <br>

                <div class="flex justify-between modal-header mb-6 mt-6">
                    <div>
                       <h1 style="color: var(--ci-primary-color);">{{ $t('Deposit') }} </h1>
                       
                    </div>
                </div> 
                <DepositWidget />
            </div>
        </div>
    </div>

</template>

<script>
    import {useAuthStore} from "@/Stores/Auth.js";
    import DepositWidget from "@/Components/Widgets/DepositWidget.vue";
    import {onMounted, ref, watch, watchEffect} from "vue";
    import {initFlowbite} from "flowbite";
    import HttpApi from "@/Services/HttpApi.js";

    import { useRouter } from 'vue-router';

    export default {
        props: ['showMobile', 'title', 'isFull'],
        components: { DepositWidget },
        data() {
            return {
                isModalOpen: true,
                isLoading: false,
                modalDeposit: null,
                isLoadingWallet: true,
                wallet: null,
            }
        },
        setup(props) {
            onMounted(() => {
                initFlowbite();
            });

            const router = useRouter();
            const isCasinoPlayPage = ref(false);

            watchEffect(() => {
                checkRoute();
            });

            onMounted(() => {
                checkRoute();
            });

            function checkRoute() {
                // Verifique se a rota atual é 'casinoPlayPage'
                isCasinoPlayPage.value = router.currentRoute._value.name === 'casinoPlayPage';
            }

            return {
                router,
                isCasinoPlayPage
            };

        },
        computed: {
            isAuthenticated() {
                const authStore = useAuthStore();
                return authStore.isAuth;
            },
        },
        mounted() {
            window.scrollTo(0, 0);
            this.modalDeposit = new Modal(document.getElementById('modalElDeposit'), {
                placement: 'center',
                backdrop: 'dynamic',
                backdropClasses: 'bg-gray-900/50 dark:bg-gray-900/80 fixed inset-0 z-1 backmodaldeposit',
                closable: true,
                onHide: () => {
                    this.paymentType = null;
                    const divsToDelete = document.querySelectorAll('.backmodaldeposit');
                    if (divsToDelete.length > 0) {
                        divsToDelete.forEach(div => {
                        div.remove();
                        });
                    }
                },
                onShow: () => {

                },
                onToggle: () => {
                    
                },
            });
        },
        beforeUnmount() {

        },
        methods: {
            getWallet: async function() {
                const _this = this;

                await HttpApi.get('profile/wallet')
                    .then(response => {
                        _this.wallet = response.data.wallet;
                        _this.isLoadingWallet = false;
                    })
                    .catch(error => {
                        Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {
                            if(value == 'unauthenticated') {
                                localStorage.clear();
                                clearInterval(this.processInterval);
                            }
                        });

                        _this.isLoadingWallet = false;
                    });
            },
            toggleModalDeposit: function() {
                // Redirecionar para /profile/deposit
                this.$router.push('/profile/deposit');
            },
        },
        async created() {
            await this.getWallet(); // Substitua 'seuMetodo' pelo nome do seu método

            
        },
        watch: {

        },
    };
</script>

<style scoped>
.rounded-button {
  width: 100px; /* Ajuste conforme necessário */
  height: 50px; /* Ajuste conforme necessário */
  border-radius: 25px; /* Faz o botão arredondado */
  border: 1px solid #ccc; /* Ajuste a cor da borda conforme necessário */
  background-color: #007bff; /* Ajuste a cor de fundo conforme necessário */
  color: white; /* Ajuste a cor do texto conforme necessário */
  font-size: 16px; /* Ajuste o tamanho da fonte conforme necessário */
  cursor: pointer;
}
</style>
