<template>
    <div class="flex sm:hidden">
        <div class="fixed z-30 w-full h-16 max-w-lg -translate-x-1/2 bottom-0 left-1/2 " style="background-color: var(--navtop-color-dark)">

             <div class="flex items-center justify-start py-3">
                    <button @click.prevent="toggleMenu" type="button"  class="inline-flex flex-col items-center justify-center px-2 rounded-r-full  group">
                        <span class="sr-only"></span>
                       <svg data-v-c42cec75="" height="1em" viewBox="0 0 448 512" width="60" xmlns="http://www.w3.org/2000/svg"><path d="M0 96C0 78.3 14.3 64 32 64H416c17.7 0 32 14.3 32 32s-14.3 32-32 32H32C14.3 128 0 113.7 0 96zM0 256c0-17.7 14.3-32 32-32H416c17.7 0 32 14.3 32 32s-14.3 32-32 32H32c-17.7 0-32-14.3-32-32zM448 416c0 17.7-14.3 32-32 32H32c-17.7 0-32-14.3-32-32s14.3-32 32-32H416c17.7 0 32 14.3 32 32z" fill="currentColor"></path></svg>
                         <span class="text-[10px]">{{ $t('Menu') }}</span>
                    </button>

                <div id="tooltip-home" role="tooltip" class="absolute z-10 invisible inline-block px-2 py-2 text-sm font-medium text-white transition-opacity duration-300 bg-gray-900 rounded-lg shadow-sm opacity-0 tooltip dark:bg-gray-700">
                    {{ $t('Menu') }}
                    <div class="tooltip-arrow" data-popper-arrow></div>
                </div>


                <button @click="$router.push('/casino/provider/all/category')" data-tooltip-target="tooltip-casino" type="button" class="inline-flex flex-col items-center justify-center px-2  group">
                    <svg height="1.10em" viewBox="0 0 20 20" width="60" xmlns="http://www.w3.org/2000/svg" fill="currentColor"> <path fill-rule="evenodd" d="M12.395 2.553a1 1 0 00-1.45-.385c-.345.23-.614.558-.822.88-.214.33-.403.713-.57 1.116-.334.804-.614 1.768-.84 2.734a31.365 31.365 0 00-.613 3.58 2.64 2.64 0 01-.945-1.067c-.328-.68-.398-1.534-.398-2.654A1 1 0 005.05 6.05 6.981 6.981 0 003 11a7 7 0 1011.95-4.95c-.592-.591-.98-.985-1.348-1.467-.363-.476-.724-1.063-1.207-2.03zM12.12 15.12A3 3 0 017 13s.879.5 2.5.5c0-1 .5-4 1.25-4.5.5 1 .786 1.293 1.371 1.879A2.99 2.99 0 0113 13a2.99 2.99 0 01-.879 2.121z" clip-rule="evenodd"></path></svg>
                  
                    <span class="text-[10px]">Todos</span>
                </button>
                <div id="tooltip-casino" role="tooltip" class="absolute z-10 invisible inline-block px-2 py-2 text-sm font-medium text-white transition-opacity duration-300 bg-gray-900 rounded-lg shadow-sm opacity-0 tooltip dark:bg-gray-700">
                    Todos
                    <div class="tooltip-arrow" data-popper-arrow></div>
                </div>



                <button @click="$router.push('/casino/provider/all/category/roletas')" data-tooltip-target="tooltip-sport" type="button" class="inline-flex flex-col items-center justify-center px-2 rounded-r-full  group">
                   <svg data-v-c42cec75="" height="1em" viewBox="0 0 512 512" width="60" xmlns="http://www.w3.org/2000/svg"><path class="primary" d="M201.9 32l-128 128h92.13l128-128H201.9zM64 32C28.65 32 0 60.65 0 96v64h6.062l128-128H64zM326.1 160l127.4-127.4C451.7 32.39 449.9 32 448 32h-86.06l-128 128H326.1zM497.7 56.19L393.9 160H512V96C512 80.87 506.5 67.15 497.7 56.19zM224.3 241.7C221.1 239.5 216.9 239.5 213.5 241.4C210.1 243.3 208 247 208 251v137.9c0 4.008 2.104 7.705 5.5 9.656C215.1 399.5 216.9 400 218.7 400c1.959 0 3.938-.5605 5.646-1.682l106.7-68.97C334.1 327.3 336 323.8 336 319.1s-1.896-7.34-5.021-9.354L224.3 241.7z" fill="currentColor"></path><path class="secondary" d="M0 160v256c0 35.35 28.65 64 64 64h384c35.35 0 64-28.65 64-64V160H0zM330.1 329.3l-106.7 68.97C222.6 399.4 220.6 400 218.7 400c-1.77 0-3.562-.4648-5.166-1.379C210.1 396.7 208 392.1 208 388.1V251c0-4.01 2.104-7.705 5.5-9.656c3.375-1.918 7.562-1.832 10.81 .3027l106.7 68.97C334.1 312.7 336 316.2 336 319.1S334.1 327.3 330.1 329.3z" fill="currentColor" opacity="0.4"></path></svg>
                    <span class="text-[10px]">Ao Vivo</span> 
                </button>
                <div id="tooltip-sport" role="tooltip" class="absolute z-10 invisible inline-block px-3 py-2 text-sm font-medium text-white transition-opacity duration-300 bg-gray-900 rounded-lg shadow-sm opacity-0 tooltip dark:bg-gray-700">
                    Ao Vivo
                    <div class="tooltip-arrow" data-popper-arrow></div>
                </div>



                <button @click="$router.push('/casino/provider/all/category/cassino')" data-tooltip-target="tooltip-sport" type="button" class="inline-flex flex-col items-center justify-center px-2 rounded-r-full  group">
                    <span data-v-c42cec75="" class="badge-live dot"></span>
                    <svg data-v-c42cec75="" height="1em" viewBox="0 0 640 512" width="60" xmlns="http://www.w3.org/2000/svg"><path d="M220.7 7.468C247.3-7.906 281.4 1.218 296.8 27.85L463.8 317.1C479.1 343.8 470 377.8 443.4 393.2L250.5 504.5C223.9 519.9 189.9 510.8 174.5 484.2L7.468 194.9C-7.906 168.2 1.218 134.2 27.85 118.8L220.7 7.468zM143.8 277.3C136.9 303.2 152.3 329.1 178.3 336.9C204.3 343.9 230.1 328.5 237.9 302.5L240.3 293.6C240.4 293.3 240.5 292.9 240.6 292.5L258.4 323.2L246.3 330.2C239.6 334 237.4 342.5 241.2 349.2C245.1 355.9 253.6 358.1 260.2 354.3L308.4 326.5C315.1 322.6 317.4 314.1 313.5 307.4C309.7 300.8 301.2 298.5 294.5 302.3L282.5 309.3L264.7 278.6C265.1 278.7 265.5 278.8 265.9 278.9L274.7 281.2C300.7 288.2 327.4 272.8 334.4 246.8C341.3 220.8 325.9 194.1 299.9 187.1L196.1 159.6C185.8 156.6 174.4 163.2 171.4 174.3L143.8 277.3z" fill="currentColor"></path><path d="M324.1 499L459.4 420.9C501.3 396.7 515.7 343.1 491.5 301.1L354.7 64.25C356.5 64.08 358.2 64 360 64H584C614.9 64 640 89.07 640 120V456C640 486.9 614.9 512 584 512H360C346.4 512 333.8 507.1 324.1 499V499zM579.8 135.7C565.8 123.9 545.3 126.2 532.9 138.9L528.1 144.2L523.1 138.9C510.6 126.2 489.9 123.9 476.4 135.7C460.7 149.2 459.9 173.1 473.9 187.6L522.4 237.6C525.4 240.8 530.6 240.8 533.9 237.6L582 187.6C596 173.1 595.3 149.2 579.8 135.7H579.8z" fill="currentColor" opacity="0.4"></path></svg>
                    <span class="text-[10px]">Cassino</span>
                </button>
                <div id="tooltip-sport" role="tooltip" class="absolute z-10 invisible inline-block px-3 py-2 text-sm font-medium text-white transition-opacity duration-300 bg-gray-900 rounded-lg shadow-sm opacity-0 tooltip dark:bg-gray-700">
                    Cassino
                    <div class="tooltip-arrow" data-popper-arrow></div>
                </div>

                
                <button @click="$router.push('/casino/provider/all/category/slots')" data-tooltip-target="tooltip-wallet" type="button" class="inline-flex flex-col items-center justify-center px-2  group">
                   <svg data-v-c42cec75="" height="1em" viewBox="0 0 640 512" width="60" xmlns="http://www.w3.org/2000/svg"><path d="M591.1 192l-118.7 0c4.418 10.27 6.604 21.25 6.604 32.23c0 20.7-7.865 41.38-23.63 57.14l-136.2 136.2v46.37C320 490.5 341.5 512 368 512h223.1c26.5 0 47.1-21.5 47.1-47.1V240C639.1 213.5 618.5 192 591.1 192zM479.1 376c-13.25 0-23.1-10.75-23.1-23.1s10.75-23.1 23.1-23.1s23.1 10.75 23.1 23.1S493.2 376 479.1 376zM96 200c-13.25 0-23.1 10.75-23.1 23.1s10.75 23.1 23.1 23.1s23.1-10.75 23.1-23.1S109.3 200 96 200zM352 248c13.25 0 23.1-10.75 23.1-23.1s-10.75-23.1-23.1-23.1S328 210.8 328 224S338.8 248 352 248zM224 328c-13.25 0-23.1 10.75-23.1 23.1s10.75 23.1 23.1 23.1c13.25 0 23.1-10.75 23.1-23.1S237.3 328 224 328zM224 200c-13.25 0-23.1 10.75-23.1 23.1s10.75 23.1 23.1 23.1s23.1-10.75 23.1-23.1S237.3 200 224 200zM224 72c-13.25 0-23.1 10.75-23.1 23.1s10.75 23.1 23.1 23.1c13.25 0 23.1-10.75 23.1-23.1S237.3 72 224 72z" fill="currentColor"></path><path d="M447.1 224c0-12.56-4.782-25.13-14.35-34.76l-174.9-174.9C249.1 4.784 236.5 0 223.1 0C211.4 0 198.9 4.784 189.2 14.35L14.35 189.2C4.784 198.9-.0011 211.4-.0011 223.1c0 12.56 4.786 25.18 14.35 34.8l174.9 174.9c9.626 9.563 22.19 14.35 34.75 14.35c12.56 0 25.13-4.782 34.75-14.35l174.9-174.9C443.2 249.1 447.1 236.6 447.1 224zM96 248c-13.25 0-23.1-10.75-23.1-23.1s10.75-23.1 23.1-23.1s23.1 10.75 23.1 23.1S109.3 248 96 248zM224 376c-13.25 0-23.1-10.75-23.1-23.1s10.75-23.1 23.1-23.1c13.25 0 23.1 10.75 23.1 23.1S237.3 376 224 376zM224 248c-13.25 0-23.1-10.75-23.1-23.1s10.75-23.1 23.1-23.1s23.1 10.75 23.1 23.1S237.3 248 224 248zM224 120c-13.25 0-23.1-10.75-23.1-23.1s10.75-23.1 23.1-23.1c13.25 0 23.1 10.75 23.1 23.1S237.3 120 224 120zM352 248c-13.25 0-23.1-10.75-23.1-23.1s10.75-23.1 23.1-23.1s23.1 10.75 23.1 23.1S365.3 248 352 248z" fill="currentColor" opacity="0.4"></path></svg>
                    <span class="text-[10px]">Slots</span>
                </button>
                <div id="tooltip-wallet" role="tooltip" class="absolute z-10 invisible inline-block px-2 py-2 text-sm font-medium text-white transition-opacity duration-300 bg-gray-900 rounded-lg shadow-sm opacity-0 tooltip dark:bg-gray-700">
                    Slots
                    <div class="tooltip-arrow" data-popper-arrow></div>
                </div>

            </div>
        </div>
    </div>
 
                    
</template>

<script>
import { RouterLink, useRoute } from "vue-router";
import { sidebarStore } from "@/Stores/SideBarStore.js";
import { Modal } from 'flowbite';
import { useAuthStore } from "@/Stores/Auth.js";
import { useToast } from "vue-toastification";
import { useRouter } from 'vue-router';

import DropdownDarkLight from "@/Components/UI/DropdownDarkLight.vue";
import LanguageSelector from "@/Components/UI/LanguageSelector.vue";
import WalletBalance from "@/Components/UI/WalletBalance.vue";
import HttpApi from "@/Services/HttpApi.js";
import MakeDeposit from "@/Components/UI/MakeDeposit.vue";
import {useSettingStore} from "@/Stores/SettingStore.js";
import {searchGameStore} from "@/Stores/SearchGameStore.js";
import CassinoGameCard from "@/Pages/Cassino/Components/CassinoGameCard.vue";

export default {
    props: ['simple'],
    components: {CassinoGameCard, MakeDeposit, WalletBalance, LanguageSelector, DropdownDarkLight, RouterLink },
    data() {
        return {
            isLoadingLogin: false,
            isLoadingRegister: false,
            isReferral: false,
            modalAuth: null,
            modalRegister: null,
            modalProfile: null,
            typeInputPassword: 'password',
            readonly: false,
            profileUser: null,
            loginForm: {
                email: '',
                password: '',
            },
            registerForm: {
                name: '',
                email: '',
                cpf: '',
                password: '',
                password_confirmation: '',
                reference_code: '',
                term_a: false,
                agreement: false,
            },
            avatarUrl: '/assets/images/profile.jpg',
            isLoadingProfile: false,
            profileName: '',
            sumBets: 0,
            totalBets: 0,
            totalEarnings: 0,
            showSearchMenu: false,
            games: null,
            searchTerm: '',
            isLoadingSearch: true,
        }
    },
    setup() {
        const router = useRouter();

        return {
            router,
        };
    },
    computed: {
        searchGameDataStore() {
            return searchGameStore();
        },
        searchGameMenu() {
            const search = searchGameStore();
            return search.getSearchGameStatus;
        },
        sidebarMenuStore() {
            return sidebarStore();
        },
        isAuthenticated() {
            const authStore = useAuthStore();
            return authStore.isAuth;
        },
        userData() {
            const authStore = useAuthStore();
            return authStore.user;
        },
        setting() {
            const authStore = useSettingStore();
            return authStore.setting;
        }
    },
    unmounted() {

    },
    mounted() {
        /*
        * $targetEl: required
        * options: optional
        */
        this.modalProfile = new Modal(document.getElementById('modalProfileEl'), {
            placement: 'center',
            backdrop: 'dynamic',
            backdropClasses: 'bg-gray-700 bg-opacity-50 dark:bg-opacity-80 fixed inset-0 z-40',
            closable: false,
            onHide: () => {

            },
            onShow: () => {

            },
            onToggle: () => {

            }
        });

        /*
        * $targetEl: required
        * options: optional
        */
        this.modalAuth = new Modal(document.getElementById('modalElAuth'), {
            placement: 'center',
            backdrop: 'dynamic',
            backdropClasses: 'bg-gray-700 bg-opacity-50 dark:bg-opacity-80 fixed inset-0 z-40',
            closable: false,
            onHide: () => {

            },
            onShow: () => {

            },
            onToggle: () => {

            }
        });

        /*
       * $targetEl: required
       * options: optional
       */
        this.modalRegister = new Modal(document.getElementById('modalElRegister'), {
            placement: 'center',
            backdrop: 'dynamic',
            backdropClasses: 'bg-gray-700 bg-opacity-50 dark:bg-opacity-80 fixed inset-0 z-40',
            closable: false,
            onHide: () => {

            },
            onShow: () => {

            },
            onToggle: () => {

            }
        });
    },
    methods: {
        toggleSearch: function() {
            this.searchGameDataStore.setSearchGameToogle();
        },
        redirectSocialTo: function() {
            return '/auth/redirect/google'
        },
        like: async function(id) {
            const _this = this;
            const _toast = useToast();
            await HttpApi.post('/profile/like/' + id, {})
                .then(response => {

                    _this.getProfile();
                    _toast.success(_this.$t(response.data.message));
                })
                .catch(error => {
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {
                        _toast.error(`${value}`);
                    });
                });
        },
        updateName: async function(event) {
            const _this = this;
            _this.isLoadingProfile = true;

            await HttpApi.post('/profile/updateName', { name: _this.profileName })
                .then(response => {
                    _this.isLoadingProfile = false;
                })
                .catch(error => {
                    const _this = this;
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {

                    });
                    _this.isLoadingProfile = false;
                });
        },
        togglePassword: function() {
            if(this.typeInputPassword === 'password') {
                this.typeInputPassword = 'text';
            }else{
                this.typeInputPassword = 'password';
            }
        },
        loginSubmit: function(event) {
            const _this = this;
            const _toast = useToast();
            _this.isLoadingLogin = true;
            const authStore = useAuthStore();

            HttpApi.post('auth/login', _this.loginForm)
                .then(async response => {
                    await new Promise(r => {
                        setTimeout(() => {
                            authStore.setToken(response.data.access_token);
                            authStore.setUser(response.data.user);
                            authStore.setIsAuth(true);

                            _this.loginForm = {
                                email: '',
                                password: '',
                            }

                            _this.modalAuth.toggle();
                            _toast.success(_this.$t('You have been authenticated, welcome!'));

                            _this.isLoadingLogin = false;
                        }, 1000)
                    });
                })
                .catch(error => {
                    const _this = this;
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {
                        _toast.error(`${value}`);
                    });
                    _this.isLoadingLogin = false;
                });
        },
        registerSubmit: async function(event) {
            const _this = this;
            const _toast = useToast();
            _this.isLoadingRegister = true;

            const authStore = useAuthStore();
            await HttpApi.post('auth/register', _this.registerForm)
                .then(response => {
                    if(response.data.access_token !== undefined) {
                        authStore.setToken(response.data.access_token);
                        authStore.setUser(response.data.user);
                        authStore.setIsAuth(true);

                        _this.registerForm = {
                            name: '',
                            email: '',
                            password: '',
                            password_confirmation: '',
                            reference_code: '',
                            term_a: false,
                            agreement: false,
                        }

                        _this.modalRegister.toggle();
                        _this.router.push({ name: 'profileDeposit' });
                        _toast.success(_this.$t('Your account has been created successfully'));
                    }

                    _this.isLoadingRegister = false;
                })
                .catch(error => {
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {
                        _toast.error(`${value}`);
                    });
                    _this.isLoadingRegister = false;
                });
        },
        logoutAccount: function() {
            const authStore = useAuthStore();
            const _toast = useToast();

            HttpApi.post('auth/logout', {})
                .then(response => {
                    authStore.logout();
                    this.router.push({ name: 'home' });

                    _toast.success(this.$t('You have been successfully disconnected'));
                })
                .catch(error => {
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {
                        console.log(value);
                        //_toast.error(`${value}`);
                    });
                });
        },
        hideLoginShowRegisterToggle: function() {
            this.modalAuth.toggle();
            this.modalRegister.toggle();
        },
        toggleMenu: function() {
            this.sidebarMenuStore.setSidebarToogle();
        },
        loginToggle: function() {
            this.modalAuth.toggle();
        },
        registerToggle: function() {
            this.modalRegister.toggle();
        },
        profileToggle: function() {
            this.modalProfile.toggle();
        },
        openFileInput() {
            this.$refs.fileInput.click();
        },
        async handleFileChange(event) {
            const file = event.target.files[0];
            const formData = new FormData();
            formData.append('avatar', file);

            const reader = new FileReader();
            reader.onload = () => {
                this.avatarUrl = reader.result;
            };
            reader.readAsDataURL(file);

            await HttpApi.post('/profile/upload-avatar', formData, {
                headers: {
                    'Content-Type': 'multipart/form-data',
                },
            }).then(response => {
                console.log('Avatar atualizado com sucesso', response.data);
            })
                .catch(error => {
                    console.error('Erro ao atualizar avatar', error);
                });
        },
        getProfile: async function() {
            const _this = this;
            _this.isLoadingProfile = true;

            await HttpApi.get('/profile/')
                .then(response => {
                    _this.sumBets = response.data.sumBets;
                    _this.totalBets = response.data.totalBets;
                    _this.totalEarnings = response.data.totalEarnings;

                    const user = response.data.user;

                    if(user?.avatar != null) {
                        _this.avatarUrl = '/storage/'+user.avatar;
                    }

                    _this.profileName = user.name;
                    _this.profileUser = user;
                    _this.isLoadingProfile = false;
                })
                .catch(error => {
                    const _this = this;
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {

                    });
                    _this.isLoadingProfile = false;
                });
        },
        getSearch: async function() {
            const _this = this;

            await HttpApi.get('/search/games?searchTerm='+this.searchTerm)
                .then(response => {
                    _this.games = response.data.games;
                    _this.isLoadingSearch = false;
                })
                .catch(error => {
                    const _this = this;
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {

                    });
                    _this.isLoadingSearch = false;
                });
        },
        clearData: async function() {
            this.searchTerm = '';
            await this.getSearch();
        }
    },
    async created() {
        if(this.isAuthenticated) {

            await this.getProfile();
        }
    },
    watch: {
        searchTerm(newValue, oldValue) {
            this.getSearch();
        },
        async searchGameMenu(newValue, oldValue) {

            await this.getSearch();
            this.showSearchMenu = !this.showSearchMenu;
        },
    },
};
</script>

<style scoped>

</style>
