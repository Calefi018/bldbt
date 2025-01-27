<style>
.L1xyJ {
    align-items: center;
    cursor: pointer;
    display: flex;
    font-size: .875rem;
    font-weight: 700;
    gap: .5rem;
    justify-content: center;
    line-height: 1.25rem;
    padding-bottom: 1rem;
    padding-top: 1rem;
    position: relative;
    text-transform: uppercase;
    width: 100%;
    --tw-text-opacity: 1;
    color: rgb(253 255 255 / var(--tw-text-opacity));
    opacity: .5;
    text-decoration-line: none;
}

.depositButtonPill[data-v-f0101099] {
    align-items: center;
    border-radius: 1.5rem;
    display: flex;
    gap: 2px;
    height: 14px;
    justify-content: center;
    position: absolute;
    right: 0;
    top: -8px;
    width: 36px;
    z-index: 10;
    --tw-bg-opacity: 1;
    background-color: rgb(255 232 0 / var(--tw-bg-opacity));
    color: #000000e6;
    font-size: 8px;
    font-weight: 700;
}

.pad-modal-profile {
    padding: 0px 4%;
}

.hover-menu:hover {
    background-color: #0F2B39;
    border-radius: 10px;
}

.sair-menu:hover {
    background-color: #27171A;
    border-radius: 10px;
    color: #D3345D;
}

.sairp-menu:hover {
    color: #D3345D;
}

.notificacao-sino {
    font-size: 20px;
    color: gold;
}

.tirar-div {
    display: none;
}

.padding-register {
    padding: 0px 8%;
}

.nav-indexx {
    z-index: 21;
    width: 8px;
}

.login-register-x {
    display: flex; /* Habilita o layout flex */
    align-items: center; /* Alinha verticalmente ao centro */
    justify-content: center; /* Alinha horizontalmente ao centro */
    height: 100%; /* Ajusta a altura conforme necessário */
    width: 100%; /* Ajusta a largura conforme necessário */
}

.login-register-100vh {
    background-color: var(--carousel-banners-dark);
    border-radius: 20px;
    max-width: 450px;
    margin: 0 auto;
    border-radius: 8px;
}

.x-mark-scale {
    transition: .3s;
}

.x-mark-scale:hover {
    transform: scale(.9);
}

.msg-alerta-text {
    color: white;
    font-weight: 400;
    font-size: 14px;
    text-align: center;
    overflow: hidden;
}

.texto-esportes {
    opacity: .5;
    transition: .3s;
}

.texto-esportes:hover {
    opacity: 1;
}

@media (max-width:1025px) {
    #open-side-nav {
        display: none;
    }

    .tirar-esporte {
        display: none;
    }
}

@media (max-width:768px) {
    .texto-indique {
        font-size: 14px;
        padding-top: 5px;
    }

    .texto-indique-pad {
        padding: 0 2%;
        text-align: center
    }

    .pad-modal-profile {
        padding: 0px 0px;
    }

    .por-height-alto {
        height: 100vh;
        border-radius: 0px;
    }

    .notificacao-sino {
        font-size: 1rem;
        font-weight: 700;
        line-height: 1.25rem;
        padding: 0px 8px;
    }

    .search-menu {
        top: 0;
        min-height: 100vh;
    }

    .imagem-logo {
        max-width: 140px
    }

    .botao-entrar-mobile {
        padding: 3px 10px;
    }

    .nav-indexx {
        z-index: 21;
    }

    .botao-mobile-register-login {
        padding: 2px 12px;
        height: auto;
    }

    .login-register-100vh {
        height: 100vh;
        border-radius: 0px;
        max-width: 1000px;
        width: 100%;
    }

    .login-register-x {
        margin-top: -10px;
        margin-right: -25px;
    }

    .padding-register {
        padding: 0px 4%;
    }
}

@media(max-width:600px) {
    .margin-teste {
        margin-left: 0px
    }

    .tirar-div {
        display: block;
    }

    .nav-small {
        width: 5px;
        /* Altere este valor conforme necessário */
        max-width: 100%;
        /* Garante que o elemento não ultrapasse o contêiner pai */
    }

    .pulse2 {
        width: 2px;
        height: 2px;
        margin-left: 15px;
        bottom: 0;
    }

    @media(max-width:500px) {
        .texto-indique {
            font-size: 12px;
            padding-top: 5px;
        }
    }
    .botaoFechar {
        position: absolute;
        top: 10px; /* Ajuste conforme necessário */
        right: 10px; /* Ajuste conforme necessário */
        z-index: 1000; /* Garante que o botão esteja acima de outros elementos */
    }
}
</style>
<template>

    <div id="promo-banner" class="fixed top-0 z-50 texto-indique-pad"
        style="background-color: var(--ci-primary-color); height: 30px; width:100%; display: flex; align-items: center; justify-content: center; padding: 8px;">
        <p class="texto-indique" style="color: var(--text-color); margin-right: 4px; font-size: 10px;">Indique um amigo e ganhe R$5,00 Bônus 🎁 </p>

        <a href="../profile/affiliate"
            style="height: 20px; padding: 1px 4px; font-size: 12px; border-radius: 3px; background-color: #212425; color: var(--ci-primary-color); text-decoration: none; margin-right: 5px;">Resgatar</a>

    </div>


    <nav v-if="showNavtop" :class="[
        sidebar === false ? 'w-full' : 'w-full',
    ]" class="fixed top-0 z-21 navtop-color nav-indexx nav-small" style="height: 90px; width: 100%;">

        <div class="px-2 lg:px-5 lg:pl-3 nav-menu relative" style="background-color: var(--navtop-color-dark);">
            <div class="absolute top-9 left-0 hidden lg:block">
                <div class="flex items-center justify-center h-full" style="align-items: center;">


                    <!-- <a href="/" class="flex-row w-[100%] cursor-pointer items-start px-2 py-3 border-primary flex justify-start">
                            <svg height="24px" viewBox="0 0 640 512" width="24px" xmlns="http://www.w3.org/2000/svg">
                                <path d="M220.7 7.468C247.3-7.906 281.4 1.218 296.8 27.85L463.8 317.1C479.1 343.8 470 377.8 443.4 393.2L250.5 504.5C223.9 519.9 189.9 510.8 174.5 484.2L7.468 194.9C-7.906 168.2 1.218 134.2 27.85 118.8L220.7 7.468zM143.8 277.3C136.9 303.2 152.3 329.1 178.3 336.9C204.3 343.9 230.1 328.5 237.9 302.5L240.3 293.6C240.4 293.3 240.5 292.9 240.6 292.5L258.4 323.2L246.3 330.2C239.6 334 237.4 342.5 241.2 349.2C245.1 355.9 253.6 358.1 260.2 354.3L308.4 326.5C315.1 322.6 317.4 314.1 313.5 307.4C309.7 300.8 301.2 298.5 294.5 302.3L282.5 309.3L264.7 278.6C265.1 278.7 265.5 278.8 265.9 278.9L274.7 281.2C300.7 288.2 327.4 272.8 334.4 246.8C341.3 220.8 325.9 194.1 299.9 187.1L196.1 159.6C185.8 156.6 174.4 163.2 171.4 174.3L143.8 277.3z" fill="currentColor"></path>
                                <path d="M324.1 499L459.4 420.9C501.3 396.7 515.7 343.1 491.5 301.1L354.7 64.25C356.5 64.08 358.2 64 360 64H584C614.9 64 640 89.07 640 120V456C640 486.9 614.9 512 584 512H360C346.4 512 333.8 507.1 324.1 499V499zM579.8 135.7C565.8 123.9 545.3 126.2 532.9 138.9L528.1 144.2L523.1 138.9C510.6 126.2 489.9 123.9 476.4 135.7C460.7 149.2 459.9 173.1 473.9 187.6L522.4 237.6C525.4 240.8 530.6 240.8 533.9 237.6L582 187.6C596 173.1 595.3 149.2 579.8 135.7H579.8z" fill="currentColor" opacity="0.4"></path>
                            </svg>
                            <p class="text-[16px] font-bold" style="padding-left: 8px;color: white">CASSINO</p>
                    </a> -->

                    <!-- <a href="games/play/10369/8357" class="flex-row w-[100%] cursor-pointer items-start px-2 py-3 border-primary flex justify-start">
                        <svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0" y="0" width="20px" height="20px" viewBox="0 0 1706.66 1706.66" xml:space="preserve" xmlns:svgjs="http://svgjs.com/svgjs">
                            <g>
                                <path d="M853.33 1706.62C382.83 1706.62.05 1323.83.05 853.34.05 382.84 382.83.06 853.33.06s853.28 382.78 853.28 853.28-382.78 853.28-853.28 853.28z" fill="currentColor" data-original="#ff7a1b"></path>
                                <g fill="#ff5329">
                                    <path d="M181.17 1378.38c-8.22-10.5-16.2-21.18-23.93-32.06l.03-.02c73.48-54.75 168.35-109.99 250.02-144.77 382.42-162.87 809.12-103.64 1142.24 144.63a841.386 841.386 0 0 1-23.92 32.06c-408.21-303.76-935.57-304.03-1344.45.15zM.31 873.34v-39.99h1706.04v39.99zM156.75 361.06c7.71-10.89 15.69-21.57 23.89-32.07 51.65 36.15 90.93 62.44 146.16 92.64 300.7 164.41 661.03 178.42 972.68 39.8 73.08-32.51 157.21-87.16 223.41-136.42a852.126 852.126 0 0 1 24.07 31.95c-59.38 46.95-167.21 113.08-235.24 143.06-320.16 141.11-693.84 125.9-1001.41-41.63-41.7-22.71-115.7-68.08-153.55-97.33z" fill="#040404" data-original="#ff5329"></path>
                                    <path d="M853.33 1706.62c-10.16 0-20.26-.24-30.33-.6-16.54-223.46 2.95-1368.56 8.42-1705.68l39.56-.06c-4.67 250.17-8.98 600.68-11.64 834.99-4.08 359.39-4.31 737.4 3.91 871.21-3.3.04-6.59.13-9.91.13z" fill="#040404" data-original="#ff5329"></path>
                                </g>
                            </g>
                        </svg>
                        <p class="text-[16px] font-bold" style="padding-left: 8px;color: white">ESPORTES</p>
                    </a> -->

                </div>
            </div>
        </div>


        <div :class="[
            sidebar === true ? 'lg:ml-[65px]' : 'lg:ml-[280px]',
        ]">
            <div class="mx-auto w-full" style="max-width: 1110px;">
                <div class="flex items-center justify-between " style="align-items: center">


                    <div class="flex items-center justify-start" style="align-items: center; margin-top: 28px;">


                        <button id="open-side-nav" @click.prevent="toggleMenu" type="button"
                            class="inline-flex items-center p-2 text-sm text-gray-500 rounded-lg"
                            style="margin-left: 40px">
                            <span class="sr-only">Open sidebar</span>

                            <svg height="22px" viewBox="0 0 448 512" width="22px" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M0 96C0 78.3 14.3 64 32 64H416c17.7 0 32 14.3 32 32s-14.3 32-32 32H32C14.3 128 0 113.7 0 96zM0 256c0-17.7 14.3-32 32-32H416c17.7 0 32 14.3 32 32s-14.3 32-32 32H32c-17.7 0-32-14.3-32-32zM448 416c0 17.7-14.3 32-32 32H32c-17.7 0-32-14.3-32-32s14.3-32 32-32H416c17.7 0 32 14.3 32 32z"
                                    fill="var(--ci-primary-color)"></path>
                            </svg>
                        </button>


                        <a href="/#">
                            <img :src="`/storage/` + setting.software_logo_black" alt=""
                                class="h-8 block dark:hidden imagem-logo" />
                            <img :src="`/storage/` + setting.software_logo_white" alt=""
                                class="md:max-h-[35px] max-h-[30px] hidden dark:block imagem-logo" />
                        </a>
                    </div>

                    <div v-if="!simple" class="flex items-center py-3">


                        <div v-if="!isAuthenticated" class="flex ml-5" style="margin-top: 28px;">
                            <button @click="redirectTo('/register')" style="color: #ACAFA7">
                                Registre-se
                            </button>
                            <button @click="redirectTo('/login')"
                                class="ui-button-blue ml-4 rounded flex flex-row items-center botao-entrar-mobile">
                                Entrar
                            </button>
                        </div>



                        <div v-if="isAuthenticated" class="flex items-center" style="margin-top: 20px;">
                            <MakeDeposit :showMobile="false" :title="$t('Depositar')" />
                            <WalletBalance />

                            <!--- <LanguageSelector />
                                <DropdownDarkLight/> --->

                            <div class="flex items-center">
                                <button type="button" class="flex text-sm bg-white rounded-full ui-button-blue3"
                                    aria-expanded="false" data-dropdown-toggle="dropdown-user2" style="margin: 0;">
                                    <span class="sr-only">Open user menu</span>
                                    <img class="w-9 h-9 rounded-full border-2 border-[var(--ci-primary-color)]"
                                        :src="userData?.avatar ? '/storage/' + userData.avatar : '/assets/images/profile.jpg'"
                                        alt="">
                                </button>


                                <div class="z-49 hidden text-left navtop-color list-none absolute top-full"
                                    id="dropdown-user2">
                                    <ul class="py-1 px-5 mt-0" role="none">

                                        <div class="flex items-center self-center justify-center w-full pt-4">

                                            <div
                                                class="text-center flex flex-col justify-center self-center items-center">
                                                <div class="relative">
                                                    <img style="max-width: 100px; width: 100px; height: 100px; border-radius: 50%;"
                                                        class=""
                                                        :src="userData?.avatar ? '/storage/' + userData.avatar : `/assets/images/profile.jpg`"
                                                        alt="">
                                                    <input ref="fileInput" type="file" style="display: none;"
                                                        @change="handleFileChange">
                                                </div>

                                                <div class="relative">
                                                    <p style="font-weight: bold"
                                                        class="text-sm font-medium text-gray-900 truncate dark:text-gray-300"
                                                        role="none">
                                                        {{ userData?.name }}
                                                    </p>

                                                    <p style="font-weight: bold"
                                                        class="text-sm font-medium text-gray-900 truncate dark:text-gray-300"
                                                        role="none">
                                                        {{ userData?.email }}
                                                    </p>
                                                </div>
                                            </div>


                                        </div>

                                        <div class=""
                                            style="height: 1px;background-color: #27292A;width: 100%;margin-top: 10px;margin-bottom: 10px">
                                        </div>


                                        <li class="hover-menu">
                                            <a style="color: var(--title-color);" href="#"
                                                @click.prevent="profileToggle"
                                                class="flex items-center block px-4 py-2 text-sm text-gray-700 dark:text-gray-300"
                                                role="menuitem">
                                                <span class="">
                                                    <i class="fa-solid fa-user-gear pr-3"></i>
                                                </span>
                                                <p style="font-weight: bold"> Perfil</p>
                                            </a>
                                        </li>
                                        
                                        <li class="hover-menu">
                                            <RouterLink style="color: var(--title-color);"
                                                :to="{ name: 'profileAffiliate' }" active-class="profile-menu-active"
                                                class="flex items-center block px-4 py-2 text-sm text-gray-700 dark:text-gray-300">
                                                <span class="">
                                                    <i class="fa-solid fa-people-group pr-3"></i>
                                                </span>
                                                <p style="font-weight: bold"> {{ $t('Painel Afiliado') }}</p>
                                            </RouterLink>
                                        </li>


                                        <li class="hover-menu">
                                            <RouterLink style="color: var(--title-color);"
                                                :to="{ name: 'profileWallet' }" active-class="profile-menu-active"
                                                class="flex items-center block px-4 py-2 text-sm text-gray-700 dark:text-gray-300">
                                                <span class="">
                                                    <i class="fa-duotone fa-wallet pr-3"></i>
                                                </span>
                                                <p style="font-weight: bold"> Carteira</p>
                                            </RouterLink>
                                        </li>
                                        <li class="hover-menu">
                                            <RouterLink style="color: var(--title-color);"
                                                :to="{ name: 'profileWithdraw' }" active-class="profile-menu-active"
                                                class="flex items-center block px-4 py-2 text-sm text-gray-700 dark:text-gray-300">
                                                <span class="">
                                                    <i class="fa-solid fa-minus pr-3"></i>

                                                </span>
                                                <p style="font-weight: bold"> Sacar</p>
                                            </RouterLink>
                                        </li>
                                        <li class="hover-menu">
                                            <RouterLink style="color: var(--title-color);"
                                                :to="{ name: 'profileDeposit' }" active-class="profile-menu-active"
                                                class="flex items-center block px-4 py-2 text-sm text-gray-700 dark:text-gray-300">
                                                <span class="">
                                                    <i class="fa-solid fa-minus pr-3"></i>
                                                </span>
                                                <p style="font-weight: bold"> Depositar</p>
                                            </RouterLink>
                                        </li>
                                        <li class="hover-menu">
                                            <RouterLink style="color: var(--title-color);"
                                                :to="{ name: 'profileTransactions' }" active-class="profile-menu-active"
                                                class="flex items-center block px-4 py-2 text-sm text-gray-700 dark:text-gray-300">
                                                <span class="">
                                                    <i class="fa-solid fa-minus pr-3"></i>

                                                </span>
                                                <p style="font-weight: bold"> Transações</p>
                                            </RouterLink>
                                        </li>
                                        
                                        <div class=""
                                            style="height: 1px;background-color: #27292A;width: 100%;margin-top: 10px;margin-bottom: 10px">
                                        </div>

                                        <li class="sair-menu mb-3">
                                            <a style="color: var(--title-color);" @click.prevent="logoutAccount"
                                                href="#"
                                                class="flex items-center block px-4 py-2 text-sm text-gray-700 dark:text-gray-300"
                                                role="menuitem">
                                                <span class="">
                                                    <i class="fa-duotone fa-right-from-bracket pr-3"></i>
                                                </span>
                                                <p> Sair</p>
                                            </a>
                                        </li>
                                    </ul>
                                </div>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </div>


        <transition name="fade">
            <div style="z-index: 999;background-color:rgba(0, 0, 0, 0.47);
                backdrop-filter: none;height: 100vh;" v-if="showSearchMenu"
                class="fixed left-0 right-0 bottom-0 flex items-center justify-center mx-auto w-full">
                <div @click="toggleSearch" class="absolute inset-0 opacity-50 cursor-pointer"></div>

                <!-- Start searchbar action -->

                <div class="search-menu mx-auto w-full relative p-4">

                    <br>
                    <br>
                    <br>
                    <div class=" w-full search-margin p-4">

                        <div class=" mx-auto">

                            <div class="flex flex-col">
                                <div class="relative w-full">
                                    <input
                                        style="-webkit-box-shadow: 0px 0px 14px -22px rgba(43,43,43,1);-moz-box-shadow: 0px 0px 14px -22px rgba(43,43,43,1);box-shadow: 0px 0px 14px -22px rgba(43,43,43,1);background-color: var(--ci-gray-dark);border-radius: 3px;font-size: 14px;padding-left: 40px;padding-top: 5px;padding-bottom: 5px;"
                                        type="search" v-model.lazy="searchTerm"
                                        class="block p-2.5 w-full z-999 text-sm text-gray-900 dark:placeholder-gray-400 dark:text-white placeholder-search p-2.5 lg:p-0 search-mobile"
                                        placeholder="Pesquise um nome de jogo." required>

                                    <button v-if="searchTerm.length > 0" @click.prevent="clearData" type="button"
                                        class="absolute end-0 h-full p-2.5 text-sm font-medium text-white">
                                    </button>

                                </div>
                                <div class="text-center mt-4 justify-center p-2"
                                    style="background-color: #383028;border-radius: 5px;">

                                    <h3 style="color: #FF9F43;font-size: .75rem;">Mínimo 3 caracteres</h3>

                                </div>
                            </div>

                            <div v-if="!isLoadingSearch" class="mt-8 grid grid-cols-4 md:grid-cols-12 gap-4 py-5">
                                <CassinoGameCard v-if="games" v-for="(game, index) in games?.data" :index="index"
                                    :title="game.game_name" :cover="game.cover" :gamecode="game.game_code"
                                    :type="game.distribution" :game="game" />
                            </div>

                            <div v-else
                                class="relative items-center block max-w-sm p-6 bg-white border border-gray-100 rounded-lg shadow-md dark:bg-gray-800 dark:border-gray-800 dark:hover:bg-gray-700">
                                <h5
                                    class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white opacity-20">
                                    Noteworthy technology acquisitions 2021</h5>
                                <p class="font-normal text-gray-700 dark:text-gray-400 opacity-20">Here are the biggest
                                    enterprise technology acquisitions of 2021 so far, in reverse chronological order.
                                </p>
                                <div role="status" class="absolute -translate-x-1/2 -translate-y-1/2 top-2/4 left-1/2">
                                    <i class="fa-duotone fa-spinner-third fa-spin"
                                        style="font-size: 45px;--fa-primary-color: var(--ci-primary-color); --fa-secondary-color: #000000;"></i>
                                    <span class="sr-only">Loading...</span>
                                </div>
                            </div>

                            <a class="login-register-x" @click.prevent="toggleSearch" href="">
                                <div class="x-mark-scale"
                                    style="box-shadow: 0px 2px 20px rgba(0, 0, 0, 0.50);background-color: var(--carousel-banners-dark);padding: 7px 13px;border-radius: 5px;max-width: 40px">
                                    <i style="color: var(--ci-primary-color);font-weight: bold" class="fa-light fa-x"></i>
                                </div>
                            </a>

                        </div>

                    </div>
                </div>
                <!-- End searchbar action -->


            </div>
        </transition>

    </nav>

    <div id="modalProfileEl" tabindex="-1" aria-hidden="true" class="fixed top-0 left-0 right-0 z-50 hidden w-full overflow-x-hidden overflow-y-auto md:inset-0 h-screen md:h-[calc(100%-1rem)] max-h-full pad-modal-profile">
        <div class="relative w-full max-w-2xl md:max-w-lg max-h-full rounded-lg shadow-lg por-height-alto" style="background-color: var(--navtop-color-dark);">
            
            <div v-if="!isLoadingProfile" class="flex flex-col">

                <!-- PROFILE HEADER -->
                <div class="flex justify-between w-full p-4 ">
                    <h1 class="text-2xl font-bold pt-2 p-4">{{ $t('Seu Perfil') }}</h1>
                    <button @click.prevent="profileToggle" type="button" class="text-1xl">
                        <div class="x-mark-scale"
                            style="box-shadow: 0px 2px 20px rgba(0, 0, 0, 0.50);background-color: #212425;padding: 7px 13px;border-radius: 5px;max-width: 40px">
                            <i style="color: var(--ci-primary-color);font-weight: bold" class="fa-light fa-x"></i>
                        </div>
                    </button>
                </div>

                <a class="login-register-x" @click.prevent="toggleSearch" href=""></a>

                <!-- PROFILE BODY -->
                <div v-if="profileUser != null" class="flex flex-col w-full p-4"
                    style="border-bottom-left-radius: 8px;border-bottom-right-radius: 8px;">

                    <!-- PROFILE INFO -->
                    <div class="flex flex-col items-center justify-center w-full pt-4">
                        <div class="text-center flex flex-col justify-center items-center">
                            <div class="relative">
                                <img style="max-width: 100px;" class="rounded-full"
                                    :src="userData?.avatar ? '/storage/' + userData.avatar : '/assets/images/profile.jpg'" alt="">
                                <input ref="fileInput" type="file" style="display: none;" @change="handleFileChange">
                                <button style="margin-right: -15px;margin-bottom: -12px; box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);" @click="openFileInput" type="button"
                                    class="absolute bottom-0 right-0 text-3xl bg-gray-800 p-2 rounded-full z-10">
                                    <i class="fa-duotone fa-camera-retro"></i>
                                </button>
                            </div>


                            <div class="relative mt-4">
                                <div class="flex justify-center items-center">
                                    <input @change.prevent="updateName" v-model="profileName" type="text" :readonly="!readonly"
                                        class="appearance-none p-2 bg-transparent text-center w-full max-w-xs"
                                        :placeholder="profileName">
                                    <button @click.prevent="readonly = !readonly" type="button"
                                        class="absolute right-0 bg-gray-200 hover:bg-gray-400 dark:bg-gray-600 hover:dark:bg-gray-700 w-8 h-8 ml-2 rounded-full flex items-center justify-center">
                                        <i v-if="!readonly" class="fa-sharp fa-light fa-pen"></i>
                                        <i v-if="readonly" class="fa-solid fa-xmark"></i>
                                    </button>
                                </div>
                                <p class="text-sm font-medium text-gray-900 truncate dark:text-gray-300 font-bold mt-2 text-center">
                                    {{ userData?.email }}
                                </p>
                            </div>

                        </div>

                        <!-- <div class="mt-4">
                            <button @click.prevent="readonly = !readonly" type="button"
                                class="bg-gray-200 hover:bg-gray-400 dark:bg-gray-600 hover:dark:bg-gray-700 w-10 h-10 rounded-full flex items-center justify-center">
                                <i v-if="!readonly" class="fa-sharp fa-light fa-pen"></i>
                                <i v-if="readonly" class="fa-solid fa-xmark"></i>
                            </button>
                        </div> -->
                    </div>


                    <div class="mt-3 shadow flex flex-col rounded-lg">
                        <div class="flex justify-between px-4 pt-4">
                            <h1><span class="mr-2"><i class="fa-solid fa-chart-mixed"></i></span> {{ $t('Statistics') }}</h1>
                        </div>
                        <div class="p-4">
                            <div class="grid grid-cols-1 gap-4">
                                <div class="bg-gray-200 dark:bg-gray-700 text-center p-4">
                                    <p class="text-[12px] whitespace-nowrap">{{ $t('Total winnings') }}</p>
                                    <p class="text-2xl font-bold overflow-hidden">{{ totalEarnings }}</p>
                                </div>
                                <div class="bg-gray-200 dark:bg-gray-700 text-center p-4">
                                    <p class="text-[12px] whitespace-nowrap">{{ $t('Total bets') }}</p>
                                    <p class="text-2xl font-bold overflow-hidden">{{ totalBets }}</p>
                                </div>
                                <div class="bg-gray-200 dark:bg-gray-700 text-center p-4">
                                    <p class="text-[12px] whitespace-nowrap">{{ $t('Total bet') }}</p>
                                    <p class="text-2xl font-bold overflow-hidden">{{ sumBets }}</p>
                                </div>
                            </div>
                        </div>
                    </div>


                    <div class="py-3 text-center">
                        <p style="font-size: 14px;font-weight: bold">Conta criada há {{ profileUser.dateHumanReadable }}
                        </p>
                    </div>

                </div>
            </div>

            <div v-if="isLoadingProfile" class="flex flex-col w-full h-full">
                <div role="status" class="absolute -translate-x-1/2 -translate-y-1/2 top-2/4 left-1/2">
                    <i class="fa-duotone fa-spinner-third fa-spin"
                        style="font-size: 45px;--fa-primary-color: var(--ci-primary-color); --fa-secondary-color: #000000;"></i>
                    <span class="sr-only">{{ $t('Loading') }}...</span>
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
import { onMounted, ref, watch, watchEffect } from "vue";

import DropdownDarkLight from "@/Components/UI/DropdownDarkLight.vue";
import LanguageSelector from "@/Components/UI/LanguageSelector.vue";
import WalletBalance from "@/Components/UI/WalletBalance.vue";
import HttpApi from "@/Services/HttpApi.js";
import MakeDeposit from "@/Components/UI/MakeDeposit.vue";
import hora from "@/Components/UI/hora.vue";
import { useSettingStore } from "@/Stores/SettingStore.js";
import { searchGameStore } from "@/Stores/SearchGameStore.js";
import CassinoGameCard from "@/Pages/Cassino/Components/CassinoGameCard.vue";
import pesquisa from "@/Pages/Home/Components/pesquisa.vue";
import suporte from "@/Components/Widgets/ic-support.svg"
import categories2 from "@/Pages/Home/Components/categories.vue";

export default {
    props: ['simple'],
    components: { CassinoGameCard, categories2, hora, suporte, pesquisa, MakeDeposit, WalletBalance, LanguageSelector, DropdownDarkLight, RouterLink },
    data() {
        return {
            sidebar: /iPhone|iPad|iPod|Android/i.test(navigator.userAgent) ? false : (localStorage.getItem('sidebarStatus') ? JSON.parse(localStorage.getItem('sidebarStatus')) : false),
            showNavtop: true,
            isLoadingLogin: false,
            isLoadingRegister: false,
            isReferral: false,
            modalAuth: null,
            modalRegister: null,
            modalProfile: null,
            modalcupom: null,
            typeInputPassword: 'password',
            readonly: false,
            profileUser: null,
            custom: null,
            modalDepositNav: null,
            loginForm: {
                email: '',
                password: '',
            },
            registerForm: {
                name: '',
                email: '',
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
    setup(props) {
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
        sidebarMenu() {
            const sidebar = sidebarStore()
            return sidebar.getSidebarStatus;
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
            backdropClasses: 'bg-black/80 fixed inset-0 z-40 backdrop-blur-md',
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
            backdropClasses: 'bg-black/80 fixed inset-0 z-40 backdrop-blur-md',
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
            backdropClasses: 'bg-black/80 fixed inset-0 z-40 backdrop-blur-md',
            closable: false,
            onHide: () => {

            },
            onShow: () => {

            },
            onToggle: () => {

            }
        });
        this.modalcupom = new Modal(document.getElementById('modalcupom'), {
            placement: 'center',
            backdrop: 'dynamic',
            backdropClasses: 'bg-black/80 fixed inset-0 z-40 backdrop-blur-md',
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
        redirectTo(route) {
            this.$router.push(route);
        },
        getSetting: function () {
            const _this = this;
            const settingStore = useSettingStore();
            const settingData = settingStore.setting;

            if (settingData) {
                _this.setting = settingData;
            }
        },
        toggleSearch: function () {
            this.searchGameDataStore.setSearchGameToogle();
        },
        redirectSocialTo: function () {
            return '/auth/redirect/google'
        },
        like: async function (id) {
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
        updateName: async function (event) {
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
        togglePassword: function () {
            if (this.typeInputPassword === 'password') {
                this.typeInputPassword = 'text';
            } else {
                this.typeInputPassword = 'password';
            }
        },
        loginSubmit: function (event) {
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

                            if (_this.isCasinoPlayPage) {
                                location.reload();
                            }
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
        registerSubmit: async function (event) {
            const _this = this;
            const _toast = useToast();
            _this.isLoadingRegister = true;

            // Função para formatar o CPF
            const formatCPF = (cpf) => {
                return cpf
                    .replace(/\D/g, '') // Remove caracteres não numéricos
                    .replace(/^(\d{3})(\d)/, '$1.$2') // Adiciona o primeiro ponto
                    .replace(/(\d{3})(\d)/, '$1.$2') // Adiciona o segundo ponto
                    .replace(/(\d{3})(\d{1,2})$/, '$1-$2'); // Adiciona o hífen
            };

            // Formata o CPF antes de salvar
            _this.registerForm.cpf = formatCPF(_this.registerForm.cpf);

            const authStore = useAuthStore();
            await HttpApi.post('auth/register', _this.registerForm)
                .then(response => {
                    if (response.data.access_token !== undefined) {
                        authStore.setToken(response.data.access_token);
                        authStore.setUser(response.data.user);
                        authStore.setIsAuth(true);

                        _this.registerForm = {
                            name: '',
                            email: '',
                            cpf: '',
                            password: '',
                            password_confirmation: '',
                            reference_code: '',
                            term_a: false,
                            agreement: false,
                        }

                        _this.modalRegister.toggle();
                        _this.router.push({ name: 'home' });
                        _toast.success(_this.$t('Your account has been created successfully'));

                        if (_this.isCasinoPlayPage) {
                            location.reload();
                        } else {
                            setTimeout(() => {

                                this.modalDepositNav = new Modal(document.getElementById('modalElDeposit'), {
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

                                this.modalDepositNav.toggle();

                            }, 2000);
                        }

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

        logoutAccount: function () {
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
        hideLoginShowRegisterToggle: function () {
            this.modalAuth.toggle();
            this.modalRegister.toggle();
        },
        hideRegisterShowCupomToggle: function () {
            this.modalRegister.toggle();
            this.modalcupom.toggle();
        },
        hideCupomShowRegisterToggle: function () {
            this.modalcupom.toggle();
            this.modalRegister.toggle();
        },
        hideRegisterShowLoginToggle: function () {
            this.modalRegister.toggle();
            this.modalAuth.toggle();
        },
        toggleMenu: function () {
            this.sidebarMenuStore.setSidebarToogle();
        },
        loginToggle: function () {
            this.modalAuth.toggle();
        },
        registerToggle: function () {
            this.modalRegister.toggle();
        },
        modalcupomToggle: function () {
            this.modalcupom.toggle();
        },
        profileToggle: function () {
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
        getProfile: async function () {
            const _this = this;
            _this.isLoadingProfile = true;

            await HttpApi.get('/profile/')
                .then(response => {
                    _this.sumBets = response.data.sumBets;
                    _this.totalBets = response.data.totalBets;
                    _this.totalEarnings = response.data.totalEarnings;

                    const user = response.data.user;

                    if (user?.avatar != null) {
                        _this.avatarUrl = '/storage/' + user.avatar;
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
        getSearch: async function () {
            const _this = this;

            await HttpApi.get('/search/games?searchTerm=' + this.searchTerm)
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
        clearData: async function () {
            this.searchTerm = '';
            await this.getSearch();
        }
    },
    async created() {
        this.getSetting();
        this.custom = custom;
        if (this.isAuthenticated) {
            await this.getProfile();
        }

        if (this.isCasinoPlayPage) {
            this.showNavtop = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent) ? false : true;
        }


    },
    watch: {
        sidebarMenu(newVal, oldVal) {
            this.sidebar = newVal;
        },
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
.item-game-container {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    /* Alinhamento à esquerda do contêiner da bolinha */
}

.online-indicator {
    margin-top: 5px;
    color: white;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    /* Alinhamento à esquerda dos itens dentro do indicador */
}

.pulse2 {
    position: absolute;
    right: 0;
    bottom: 8%;
    margin-left: 12px;
    /* Ajuste conforme necessário para alinhar com o card */
    width: 10px;
    height: 10px;
    background-color: #00ff00;
    border-radius: 50%;
    margin-right: 3px;
    box-shadow: 0 0 5px #00ff00, 0 0 20px #00ff00;
}

.rounded-button {
    width: 100px;
    /* Ajuste conforme necessário */
    height: 50px;
    /* Ajuste conforme necessário */
    border-radius: 25px;
    /* Faz o botão arredondado */
    border: 1px solid #ccc;
    /* Ajuste a cor da borda conforme necessário */
    background-color: #007bff;
    /* Ajuste a cor de fundo conforme necessário */
    color: white;
    /* Ajuste a cor do texto conforme necessário */
    font-size: 16px;
    /* Ajuste o tamanho da fonte conforme necessário */
    cursor: pointer;
}

.MB01P {
    position: relative;
    display: inline-block;
    /* Mantém o tamanho do contêiner baseado no conteúdo */
}

._7ZBwU {
    width: 32px;
    /* Define o tamanho do contêiner */
    height: 32px;
    /* Define o tamanho do contêiner */
    position: relative;
}

.circle-image {
    width: 100%;
    /* Ajusta o tamanho da imagem para preencher o contêiner */
    height: 100%;
    /* Ajusta o tamanho da imagem para preencher o contêiner */
    border-radius: 50%;
    /* Faz com que a imagem tenha bordas arredondadas */
    object-fit: cover;
    /* Garante que a imagem cubra o círculo sem distorcer */
    position: absolute;
    /* Faz com que a imagem se sobreponha ao contêiner */
    top: 0;
    left: 0;
}

svg2 {
    position: absolute;
    /* Posiciona o SVG sobre o contêiner */
    top: 0;
    left: 0;
    width: 100%;
    /* Ajusta o tamanho do SVG para preencher o contêiner */
    height: 100%;
    /* Ajusta o tamanho do SVG para preencher o contêiner */
}

button {
    background-color: transparent;
    border: none;
    cursor: pointer;

}

button.clicked {
    background-color: gray;
    /* Cor de fundo quando clicado */
}

.flex-row {
    display: flex;
    flex-direction: row;
}


.cursor-pointer {
    cursor: pointer;
}

.items-center {
    align-items: center;
}

.px-2 {
    padding-left: 8px;
    padding-right: 8px;
}

.py-3 {
    padding-top: 12px;
    padding-bottom: 12px;
}

.flex {
    display: flex;
}

.justify-center {
    justify-content: center;
}

.tirar-esporte {
    border-bottom: 0px solid;
    margin-left: 10px;
    margin-top: 10px;
    padding-left: 10px;
    padding-right: 10px;
    padding-bottom: 1em;
}
</style>
