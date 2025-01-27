<style>
.btn-scroll-top {
    position: relative;
    z-index: 2;
    bottom: 2em;
    display: none;
    align-items: center;
    /* Outras propriedades de estilo aqui */
    background-color: #000000b3;
    border: 1px solid rgba(65, 105, 225, .7);
    color: #fff;
    cursor: pointer;
    transition: opacity 0.3s;
    font-size: 13px;
    gap: 0.5em;
    padding: 6px 12px;
    border-radius: 20px;
    margin-top: -30px;
    left: 48.5%;
    transform: translateX(-50%);
}

.categories-margin {
    margin-bottom: 15px;
}

.show-btn-scroll-top {
    display: block;
    display: flex;
}

.search-mobile {
    -webkit-box-shadow: 0px 0px 14px -22px rgba(43, 43, 43, 1);
    -moz-box-shadow: 0px 0px 14px -22px rgba(43, 43, 43, 1);
    box-shadow: 0px 0px 14px -22px rgba(43, 43, 43, 1);
    background-color: var(--ci-gray-dark);
    border-radius: 3px;
    font-size: 14px;
    padding-left: 40px;
    padding-top: 10px;
    padding-bottom: 10px;
}

.margin-search {
    margin-top: -6px;
}

.placeholder-search::placeholder {
    color: #ACAFAF;
    font-size: 13px;
}

@media(max-width:1024px) {
    .btn-scroll-top {
        bottom: 5em;
        padding: 2px 7px;
    }

    .margin-categorias {
        margin-top: -20px;
    }

    .item-sombra2 {
        position: relative;

    }

    .item-sombra2:after {
        content: "";
        position: absolute;
        bottom: 0;
        margin-right: -1px;
        right: 0;
        width: 25px;
        height: 100%;
        background: linear-gradient(to right, rgb(33 36 37 / 0%), var(--carousel-banners));
    }
}

.padding-mobile-banner {
    padding-top: 100px;
}

@media (max-width:768px) {
    .categories-margin {
        margin-top: 0px;
    }

    #svg-lupa {
        margin-top: -2px;
    }

    .search-mobile {
        padding-top: 8px;
        padding-bottom: 8px;
    }

    .margin-search {
        margin-top: 0px;
    }

    .padding-mobile-banner {
        padding: 0;
        padding-top: 40px;
    }
    
}
</style>
<template>


    <BaseLayout>
        <LoadingComponent :isLoading="isLoading">
            <div class="text-center">

            </div>
        </LoadingComponent>

        <div v-if="!isLoading" class="">

            <!-- Banners carousel -->
            <div class="carousel-banners">
                <div class="mx-auto w-full sm:max-w-[690px] lg:max-w-[1110px] p-4 padding-mobile-banner">

                    <div class="mx-auto w-full"
                        style="position: fixed; bottom: 0; right: 0; z-index: 2; pointer-events: auto; height: 100px; display: flex; justify-content: center; align-items: center;">
                        <button style="pointer-events: auto;" class="btn-scroll-top" @click="scrollToTop">
                            <div>
                                <svg height="1em" viewBox="0 0 384 512" width="1em" xmlns="http://www.w3.org/2000/svg">
                                    <path
                                        d="M214.6 41.4c-12.5-12.5-32.8-12.5-45.3 0l-160 160c-12.5 12.5-12.5 32.8 0 45.3s32.8 12.5 45.3 0L160 141.2V448c0 17.7 14.3 32 32 32s32-14.3 32-32V141.2L329.4 246.6c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3l-160-160z"
                                        fill="currentColor"></path>
                                </svg>
                            </div>
                            <div></div>
                        </button>
                    </div>




                    <div class="">
                        <Carousel v-bind="settings" :breakpoints="breakpoints" ref="carouselBanner">
                            <Slide v-for="(banner, index) in banners" :key="index">
                                <div class="carousel__item w-full">
                                    <a :href="banner.link" class="w-full h-full bg-blue-800">
                                        <img :src="`/storage/` + banner.image" alt="" class="h-full w-full"
                                            style="max-height: 413px">
                                    </a>
                                </div>
                            </Slide>
                        </Carousel>
                    </div>


                </div>
            </div>

            <div class=" mx-auto p-4 sm:max-w-[690px] lg:max-w-[1110px]">

                <!-- Searchbar action -->
                <div class="mx-auto sm:max-w-[690px] lg:max-w-[1110px] w-full search-margin">
                    <div class=" cursor-pointer w-full margin-search" style="margin-bottom: 39px;">
                        <div class="flex">
                            <div class="relative w-full">
                                <button @click="toggleSearch" type="submit"
                                    class="absolute top-0 start-0 h-full p-2.5 text-sm font-medium text-white rounded-e-lg">
                                    <svg id="svg-lupa" data-v-49f1cded="" height="14px" viewBox="0 0 512 512"
                                        width="14px" xmlns="http://www.w3.org/2000/svg" class="text-texts w-5 p-0 m-0"
                                        style="width: 20px; height: 16px;">
                                        <path
                                            d="M500.3 443.7l-119.7-119.7c-15.03 22.3-34.26 41.54-56.57 56.57l119.7 119.7c15.62 15.62 40.95 15.62 56.57 0C515.9 484.7 515.9 459.3 500.3 443.7z"
                                            fill="currentColor"></path>
                                        <path
                                            d="M207.1 0C93.12 0-.0002 93.13-.0002 208S93.12 416 207.1 416s208-93.13 208-208S322.9 0 207.1 0zM207.1 336c-70.58 0-128-57.42-128-128c0-70.58 57.42-128 128-128s128 57.42 128 128C335.1 278.6 278.6 336 207.1 336z"
                                            fill="currentColor" opacity="0.4"></path>
                                    </svg>
                                    <span class="sr-only">Search</span>
                                </button>
                                <input class="w-full placeholder-search p-2.5 lg:p-0 search-mobile"
                                    @click.prevent="toggleSearch" type="search" readonly
                                    placeholder="Pesquise um nome de jogo." required>

                            </div>
                        </div>
                    </div>
                </div>


                <!-- Categories -->
                <div class="mb-4 xl:mb-11">
                    <ul class="flex items-start justify-between gap-3 overflow-y-scroll">

                        <li class="site-filter-item cursor-pointer hover:opacity-80">
                            <a
                                href="/casino/provider/all/category/populares"
                                class="flex flex-col items-center justify-center">
                                <div
                                    class="mb-2 flex h-[60px] w-[60px] items-center justify-center rounded-full bg-[var(--ci-primary-opacity-color)]">
                                    <svg width="30" height="30" viewBox="0 0 512 512"
                                        xmlns="http://www.w3.org/2000/svg">
                                        <g clip-path="url(#clip0_14_23)">
                                            <path
                                                d="M425.68 179.527L332.646 86.496C324.219 78.068 310.555 78.068 302.127 86.496L279.547 109.076C257.207 100.879 233.182 96.176 208 96.176C93.125 96.176 0 189.301 0 304.176S93.125 512.176 208 512.176S416 419.051 416 304.176C416 278.994 411.297 254.967 403.1 232.627L425.68 210.049C434.107 201.621 434.107 187.957 425.68 179.527ZM208 192.176C146.25 192.176 96 242.426 96 304.176C96 313.019 88.844 320.176 80 320.176S64 313.019 64 304.176C64 224.769 128.594 160.176 208 160.176C216.844 160.176 224 167.332 224 176.176S216.844 192.176 208 192.176Z"
                                                fill="var(--ci-primary-color)">
                                            </path>
                                            <path
                                                d="M380.823 108.576L368 121.399L390.602 144L403.425 131.177C409.669 124.934 409.669 114.82 403.425 108.576S387.067 102.333 380.823 108.576ZM509.056 59.169L469.381 42.625L452.837 2.954C452.025 1.321 449.894 0 448.074 0C446.252 0 444.119 1.321 443.307 2.954L426.763 42.625L387.09 59.169C385.469 59.98 384.148 62.113 384.148 63.933C384.148 65.744 385.469 67.888 387.09 68.7L426.763 85.243L443.307 124.913C444.119 126.546 446.252 127.868 448.074 127.868C449.894 127.868 452.025 126.546 452.837 124.913L469.381 85.243L509.056 68.7C510.679 67.888 512 65.744 512 63.933C512 62.113 510.679 59.98 509.056 59.169Z"
                                                fill="var(--ci-primary-color)" opacity="0.4">
                                            </path>
                                        </g>
                                        <defs>
                                            <clipPath id="clip0_14_23">
                                                <rect width="800" height="800" fill="white">

                                                </rect>
                                            </clipPath>
                                        </defs>
                                    </svg>
                                </div>
                                <span
                                    class="flex flex-col items-center justify-center text-center text-xs font-bold text-white lg:text-sm">Populares
                                    <span class="text-[10px] font-normal lg:text-xs">

                                    </span>
                                </span>
                            </a>
                        </li>

                        <li class="site-filter-item cursor-pointer hover:opacity-80">
                            <a href="/games/play/13346/fortune-tiger"
                                class="flex flex-col items-center justify-center">
                                <div
                                    class="mb-2 flex h-[60px] w-[60px] items-center justify-center rounded-full bg-[var(--ci-primary-opacity-color)]">
                                    <svg width="30" height="30" viewBox="0 0 512 512"
                                        xmlns="http://www.w3.org/2000/svg">
                                        <g clip-path="url(#clip0_14_29)">
                                            <path
                                                d="M256 256C176.625 256 64 378.75 64 456.25C64 491.125 90.75 512 135.75 512C184.625 512 216.875 486.875 256 486.875C295.5 486.875 327.875 512 376.25 512C421.25 512 448 491.125 448 456.25C448 378.75 335.375 256 256 256Z"
                                                fill="var(--ci-primary-color)">

                                            </path>
                                            <path
                                                d="M193.5 222.625C224.375 214.5 239.875 172.625 228 129.25C221.5 105.375 208 86.25 192 75V0L128 80C113 97.75 107.5 127.75 116 158.75C127.875 202.125 162.5 230.75 193.5 222.625ZM318.5 222.625C349.5 230.75 384.125 202.125 396 158.75C404.5 127.75 399 97.75 384 80L320 0V75C304 86.25 290.5 105.375 284 129.25C272.125 172.625 287.625 214.5 318.5 222.625ZM108.75 243.375C101.5 219.375 83.875 201.5 64 194.875V128L18.5 190.375C6.5 206.875 0 226.75 0 247.125C0 254.001 1.125 261.25 3.25 268.625C13.625 303.25 45.75 325.75 74.875 318.75S119.125 278.001 108.75 243.375ZM493.5 190.375L448 128V195C428.125 201.5 410.5 219.375 403.25 243.375C392.875 278.001 408 311.75 437.125 318.75S498.375 303.25 508.75 268.625C510.875 261.375 512 254.125 512 247.125C512 226.75 505.5 206.875 493.5 190.375Z"
                                                fill="var(--ci-primary-color)" opacity="0.4"></path>


                                        </g>
                                        <defs>
                                            <clipPath id="clip0_14_29">
                                                <rect width="800" height="800" fill="white">

                                                </rect>
                                            </clipPath>
                                        </defs>
                                    </svg>
                                </div>
                                <span
                                    class="flex flex-col items-center justify-center text-center text-xs font-bold text-white lg:text-sm">Fortune
                                    <span class="text-[10px] font-normal lg:text-xs">Tiger</span>
                                </span>
                            </a>
                        </li>

                        <li class="site-filter-item cursor-pointer hover:opacity-40">
                            <a href="/casino/provider/all/category/esportes"
                                class="flex flex-col items-center justify-center">
                                <div
                                    class="mb-2 flex h-[60px] w-[60px] items-center justify-center rounded-full bg-[var(--ci-primary-opacity-color)]">
                                    <svg height="30" viewBox="0 0 512 512" width="30"
                                        xmlns="http://www.w3.org/2000/svg">
                                        <path
                                            d="M177.1 228.6L207.9 320h96.5l29.62-91.38L256 172.1L177.1 228.6zM255.1 0C114.6 0 .0001 114.6 .0001 256S114.6 512 256 512s255.1-114.6 255.1-255.1S397.4 0 255.1 0zM435.2 361.1l-103.9-1.578l-30.67 99.52C286.2 462.2 271.3 464 256 464s-30.19-1.773-44.56-4.93L180.8 359.6L76.83 361.1c-14.93-25.35-24.79-54.01-27.8-84.72L134.3 216.4L100.7 118.1c19.85-22.34 44.32-40.45 72.04-52.62L256 128l83.29-62.47c27.72 12.17 52.19 30.27 72.04 52.62L377.7 216.4l85.23 59.97C459.1 307.1 450.1 335.8 435.2 361.1z"
                                            fill="var(--ci-primary-color)"></path>
                                        <path
                                            d="M458.3 99.08L458.3 99.08L458.3 99.08zM511.8 264c-1.442 48.66-16.82 95.87-44.28 136.1l-7.38-32.46l-113 13.86l-48.19 103.3l28.22 16.84c-23.48 6.78-47.67 10.2-71.85 10.2c-23.76 0-47.51-3.302-70.58-9.962l28.23-17.06l-48.19-103.3l-113-13.88l-7.39 32.46c-27.45-40.19-42.8-87.41-44.25-136.1l24.95 21.76l83.2-77.67L86.78 96.15L53.67 99.09c29.72-38.29 69.67-67.37 115.2-83.88l.3613 .2684L156.5 45.53l99.5 55.13l99.5-55.13L342.4 14.98c45.82 16.48 86 45.64 115.9 84.11L425.6 96.16L403.7 208.2l83.21 77.67L511.8 264zM357.3 217.4L255.1 144L154.7 217.4l38.82 118.6L318.8 336L357.3 217.4z"
                                            opacity="0.0">

                                        </path>
                                    </svg>
                                </div>
                                <span
                                    class="flex flex-col items-center justify-center text-center text-xs font-bold text-white lg:text-sm">Esportes
                                    <span class="text-[10px] font-normal lg:text-xs"></span></span>
                            </a>
                        </li>

                        <li class="site-filter-item cursor-pointer hover:opacity-80">
                            <a
                                href="/casino/provider/all/category/all"
                                class="flex flex-col items-center justify-center">
                                <div
                                    class="mb-2 flex h-[60px] w-[60px] items-center justify-center rounded-full bg-[var(--ci-primary-opacity-color)]">
                                    <svg width="30" height="30" viewBox="0 0 640 512"
                                        xmlns="http://www.w3.org/2000/svg">
                                        <g clip-path="url(#clip0_14_17)">
                                            <path
                                                d="M171.4 174.3C174.4 163.2 185.8 156.6 196.1 159.6L299.9 187.1C325.9 194.1 341.3 220.8 334.4 246.8C327.4 272.8 300.7 288.2 274.7 281.2L265.9 278.9C265.5 278.8 265.1 278.7 264.7 278.6L282.5 309.3L294.5 302.4C301.2 298.5 309.7 300.8 313.5 307.4C317.4 314.1 315.1 322.6 308.4 326.5L260.2 354.3C253.6 358.1 245.1 355.9 241.2 349.2C237.4 342.5 239.6 334 246.3 330.2L258.4 323.2L240.6 292.5C240.5 292.9 240.4 293.3 240.3 293.6L237.9 302.5C230.1 328.5 204.3 343.9 178.3 336.9C152.3 329.1 136.9 303.2 143.8 277.3L171.4 174.3zM220.7 7.468C247.3-7.906 281.4 1.218 296.8 27.85L463.8 317.1C479.1 343.8 470 377.8 443.4 393.2L250.5 504.5C223.9 519.9 189.9 510.8 174.5 484.2L7.468 194.9C-7.906 168.2 1.218 134.2 27.85 118.8L220.7 7.468zM244.7 49.04L51.85 160.4C48.18 162.5 46.92 167.2 49.04 170.9L216.1 460.2C218.2 463.8 222.9 465.1 226.5 462.1L419.4 351.6C423.1 349.5 424.3 344.8 422.2 341.1L255.2 51.85C253.1 48.18 248.4 46.92 244.7 49.04H244.7zM324.1 499L459.4 420.9C501.3 396.7 515.7 343.1 491.5 301.1L354.7 64.25C356.5 64.08 358.2 63.1 360 63.1H584C614.9 63.1 640 89.07 640 119.1V456C640 486.9 614.9 512 584 512H360C346.4 512 333.8 507.1 324.1 498.1L324.1 499zM579.8 135.7C565.8 123.9 545.3 126.2 532.9 138.9L528.1 144.2L523.1 138.9C510.6 126.2 489.9 123.9 476.4 135.7C460.7 149.2 459.9 173.1 473.9 187.6L522.4 237.6C525.4 240.8 530.6 240.8 533.9 237.6L582 187.6C596 173.1 595.3 149.2 579.8 135.7H579.8z"
                                                fill="var(--ci-primary-color)">
                                            </path>

                                        </g>
                                        <defs>
                                            <clipPath id="clip0_14_17">
                                                <rect width="800" height="800" fill="white">
                                                </rect>
                                            </clipPath>
                                        </defs>
                                    </svg>
                                </div>
                                <span
                                    class="flex flex-col items-center justify-center text-center text-xs font-bold text-white lg:text-sm">Todos
                                    <span class="text-[10px] font-normal lg:text-xs">
                                    </span>
                                </span>
                            </a>
                        </li>

                        <li class="site-filter-item cursor-pointer hover:opacity-80">
                            <a href="/casino/provider/all/category/live"
                                class="flex flex-col items-center justify-center">
                                <div
                                    class="mb-2 flex h-[60px] w-[60px] items-center justify-center rounded-full bg-[var(--ci-primary-opacity-color)]">
                                    <svg width="30" height="30" viewBox="0 0 640 512"
                                        xmlns="http://www.w3.org/2000/svg">
                                        <g clip-path="url(#clip0_14_20)">
                                            <path
                                                d="M575.1 192h-102.2c3.551 10.11 5.748 20.73 5.748 31.77c0 25.64-9.984 49.75-28.12 67.89L320 423.2v24.84C320 483.3 348.7 512 383.1 512h191.1c35.35 0 63.1-28.65 63.1-63.1v-191.1C639.1 220.7 611.3 192 575.1 192zM479.1 376c-13.25 0-23.1-10.75-23.1-23.1c0-13.26 10.75-23.1 23.1-23.1s23.1 10.74 23.1 23.1C503.1 365.3 493.3 376 479.1 376zM447.5 223.8c0-16.38-6.249-32.76-18.75-45.26L269 18.73C256.5 6.238 240.3 0 223.1 0S191 6.238 178.5 18.73l-159.8 159.8C6.235 191-.0011 207.6-.0011 223.1s6.236 32.57 18.73 45.06l159.8 159.8c12.5 12.5 28.88 18.74 45.26 18.74s32.76-6.248 45.25-18.74l159.8-159.8C441.3 256.5 447.5 240.1 447.5 223.8zM394.9 235.1l-159.8 159.8c-4.076 4.076-8.838 4.686-11.31 4.686c-2.477 0-7.238-.6094-11.31-4.686L52.67 235.1C48.59 231 47.99 226.2 47.99 223.8s.6074-7.236 4.686-11.31l159.8-159.8c4.082-4.08 8.844-4.689 11.32-4.689s7.234 .6094 11.31 4.687l159.8 159.8c4.078 4.078 4.687 8.84 4.687 11.31S398.9 231 394.9 235.1zM223.8 301.6c-12.79 0-23.1 10.29-23.1 23.1c0 13.76 11.25 23.1 23.1 23.1c13.73 0 24-11.22 24-23.1C247.8 312.8 237.5 301.6 223.8 301.6zM223.8 199.8c-13.76 0-23.1 11.25-23.1 23.1c0 12.84 10.34 23.1 23.1 23.1c13.71 0 24-11.21 24-23.1C247.8 210.1 237.5 199.8 223.8 199.8zM121.9 199.8c-13.76 0-24 11.25-24 23.1c0 12.79 10.29 23.1 24 23.1c13.71 0 23.1-11.2 23.1-23.1C145.9 210.1 135.7 199.8 121.9 199.8zM325.6 199.8c-13.76 0-24 11.25-24 23.1c0 12.79 10.29 23.1 24 23.1c13.71 0 24-11.21 24-23.1C349.6 210.1 339.3 199.8 325.6 199.8zM223.8 97.94c-12.79 0-23.1 10.29-23.1 23.1c0 13.76 11.25 23.1 23.1 23.1c13.73 0 24-11.22 24-23.1C247.8 109.1 237.5 97.94 223.8 97.94z"
                                                fill="var(--ci-primary-color)">

                                            </path>

                                        </g>
                                        <defs>
                                            <clipPath id="clip0_14_20">
                                                <rect width="800" height="800" fill="white">

                                                </rect>
                                            </clipPath>
                                        </defs>
                                    </svg>
                                </div>
                                <span
                                    class="flex flex-col items-center justify-center text-center text-xs font-bold text-white lg:text-sm">Cassino
                                    <span class="text-[10px] font-normal lg:text-xs">Live</span>
                                </span>
                            </a>
                        </li>

                        <li class="site-filter-item cursor-pointer hover:opacity-80">
                            <a href="/casino/provider/all/category/slots"
                                class="flex flex-col items-center justify-center">
                                <div
                                    class="mb-2 flex h-[60px] w-[60px] items-center justify-center rounded-full bg-[var(--ci-primary-opacity-color)]">
                                    <svg height="30" viewBox="0 0 640 512" width="30"
                                        xmlns="http://www.w3.org/2000/svg">
                                        <path
                                            d="M639.1 357.2c0-6.198-.4631-12.49-1.421-18.83l-27.5-181.3C603.5 107.4 581.8 32 319.1 32C57.05 32 36.44 106.9 28.83 157.1l-27.37 181.3C.4734 344.8 0 351.1 0 357.4C0 423.9 53.35 480 121.2 480c46.12-.125 88.37-26.5 108.6-68L243.6 384h152.7l13.75 28c20.25 41.5 62.25 67.88 108.4 68C586.5 480 639.1 423.8 639.1 357.2zM591.1 357.2c0 17.99-6.413 35.55-18.26 49.46c-13.66 16.14-33.73 25.38-54.82 25.38c-.1417 0-.2834-.0004-.4252-.0013c-27.75 0-52.75-15.75-65.25-41.13l-18.32-37.05C429.5 342.9 418.4 336 406.2 336H233.7c-12.17 0-23.29 6.907-28.69 17.82l-18.32 37.05c-4.671 9.482-23.54 41.13-65.92 41.13c-21.09 0-41.04-9.357-54.58-25.38c-11.85-13.91-18.26-31.47-18.26-49.46c0-3.839 .292-7.697 .8855-11.54l27.5-181.3C81.2 132.5 104.1 107.5 134.8 100.6C195.8 86.88 257.9 80 319.1 80s124.2 6.875 185.1 20.62c30.75 6.875 53.62 31.88 58.5 63.75l27.5 181.3C591.7 349.5 591.1 353.3 591.1 357.2zM399.1 240c-17.62 0-31.1 14.38-31.1 32s14.37 32 31.1 32s31.1-14.38 31.1-32S417.6 240 399.1 240zM247.1 200l-31.96-.011L215.1 168c0-13.2-10.78-24-23.98-24C178.8 144 167.1 154.8 167.1 168l.0367 31.99L135.1 200c-13.2 0-23.98 10.8-23.98 24c0 13.2 10.77 24 23.98 24l32.04-.0098L167.1 280c0 13.2 10.82 24 24.02 24c13.2 0 23.98-10.8 23.98-24l.0368-32.01L247.1 248c13.2 0 24.02-10.8 24.02-24C271.1 210.8 261.2 200 247.1 200zM463.1 144c-17.62 0-31.1 14.38-31.1 32s14.37 32 31.1 32c17.62 0 31.1-14.38 31.1-32S481.6 144 463.1 144z"
                                            fill="var(--ci-primary-color)">
                                        </path>

                                    </svg>
                                </div>
                                <span
                                    class="flex flex-col items-center justify-center text-center text-xs font-bold text-white lg:text-sm">Slots
                                </span>
                            </a>
                        </li>
                        
                        <!-- <li class="site-filter-item cursor-pointer hover:opacity-80">
                            <a href="/games/play/332/12559" class="flex flex-col items-center justify-center">
                                <div
                                    class="mb-2 flex h-[60px] w-[60px] items-center justify-center rounded-full bg-[var(--ci-primary-opacity-color)]">
                                    <svg width="30" height="30" viewBox="0 0 512 512"
                                        xmlns="http://www.w3.org/2000/svg">
                                        <g clip-path="url(#clip0_14_32)">
                                            <path
                                                d="M256 .0003C304.1 .0003 336 73.89 336 111.8V153.8L496 253.6C506 259.6 512 269.6 512 281.6V346.5C512 356.5 508 366.5 500 372.5C492 378.4 480.1 380.4 471 377.4L336 334.5V359.5L388 398.4C396 404.4 400 413.4 400 423.4V480.3C400 489.3 396 499.3 388 505.3C380 511.3 370 513.2 360 510.3L256 480.3L152 511.3C143 513.2 133 511.3 125 505.3C117 499.3 112 489.3 112 480.3V423.4C112 413.4 117 404.4 125 398.4L176 359.5V334.5L41 377.4C32 380.4 21 378.4 13 372.5C5 366.5 0 356.5 0 346.5V281.6C0 270.6 7 258.6 16 254.6L176 154.8V112.8C176 73.89 208 0 256 0V.0003zM256 48.93C246 50.93 224 86.87 224 112.8V180.7L48 290.6V324.5L224 269.6V383.4L160 431.4V458.3L256 430.4L352 458.3V431.4L288 383.4V269.6L464 324.5V290.6L288 180.7V112.8C288 85.87 267 49.93 256 48.93V48.93z"
                                                fill="var(--ci-primary-color)">

                                            </path>

                                        </g>
                                        <defs>
                                            <clipPath id="clip0_14_32">
                                                <rect width="800" height="800" fill="white">
                                                </rect>
                                            </clipPath>
                                        </defs>
                                    </svg>
                                </div>
                                <span
                                    class="flex flex-col items-center justify-center text-center text-xs font-bold text-white lg:text-sm">Aviator
                                    <span class="text-[10px] font-normal lg:text-xs"></span>
                                </span>
                            </a>
                        </li> -->

                        <!-- <li class="site-filter-item cursor-pointer hover:opacity-80">
                            <a href="/casino/provider/all/category/spaceman"
                                class="flex flex-col items-center justify-center">
                                <div
                                    class="mb-2 flex h-[60px] w-[60px] items-center justify-center rounded-full bg-[var(--ci-primary-opacity-color)]">
                                    <svg width="30" height="30" viewBox="0 0 512 512"
                                        xmlns="http://www.w3.org/2000/svg">
                                        <g clip-path="url(#clip0_14_35)">
                                            <path
                                                d="M408 143.1C408 166.1 390.1 183.1 368 183.1C345.9 183.1 328 166.1 328 143.1C328 121.9 345.9 103.1 368 103.1C390.1 103.1 408 121.9 408 143.1zM384 312.1V394.2C384 419.7 370.6 443.2 348.7 456.2L260.2 508.6C252.8 513 243.6 513.1 236.1 508.9C228.6 504.6 224 496.6 224 488V373.3C224 350.6 215 328.1 199 312.1C183 296.1 161.4 288 138.7 288H24C15.38 288 7.414 283.4 3.146 275.9C-1.123 268.4-1.042 259.2 3.357 251.8L55.83 163.3C68.79 141.4 92.33 127.1 117.8 127.1H199.9C281.7-3.798 408.8-8.546 483.9 5.272C495.6 7.411 504.6 16.45 506.7 28.07C520.5 103.2 515.8 230.3 384 312.1V312.1zM197.9 253.9C210.8 260.2 222.6 268.7 232.1 279C243.3 289.4 251.8 301.2 258.1 314.1C363.9 284.1 414.8 234.5 439.7 188C464.7 141.3 466.1 90.47 461.7 50.33C421.5 45.02 370.7 47.34 323.1 72.33C277.5 97.16 227.9 148.1 197.9 253.9H197.9zM41.98 345.5C76.37 311.1 132.1 311.1 166.5 345.5C200.9 379.9 200.9 435.6 166.5 470C117 519.5 .4765 511.5 .4765 511.5C.4765 511.5-7.516 394.1 41.98 345.5V345.5zM64.58 447.4C64.58 447.4 103.3 450.1 119.8 433.6C131.2 422.2 131.2 403.6 119.8 392.2C108.3 380.8 89.81 380.8 78.38 392.2C61.92 408.7 64.58 447.4 64.58 447.4z"
                                                fill="var(--ci-primary-color)"> </path>

                                        </g>
                                        <defs>
                                            <clipPath id="clip0_14_35">
                                                <rect width="800" height="800" fill="white">
                                                </rect>
                                            </clipPath>
                                        </defs>
                                    </svg>
                                </div>
                                <span
                                    class="flex flex-col items-center justify-center text-center text-xs font-bold text-white lg:text-sm">Spaceman
                                    <span class="text-[10px] font-normal lg:text-xs"></span>
                                </span>
                            </a>
                        </li> -->

                        <!-- <li class="site-filter-item cursor-pointer hover:opacity-80">
                            <a href="/casino/provider/all/category/blackjack"
                                class="flex flex-col items-center justify-center">
                                <div
                                    class="mb-2 flex h-[60px] w-[60px] items-center justify-center rounded-full bg-[var(--ci-primary-opacity-color)]">
                                    <svg width="30" height="30" viewBox="0 0 384 512"
                                        xmlns="http://www.w3.org/2000/svg">
                                        <path
                                            d="M175 141.2C184.4 131.8 199.6 131.8 208.1 141.2L291.3 223.5C313.2 245.4 313.2 280.8 291.3 302.7C269.5 324.6 234 324.6 212.1 302.7L208.1 299.5C208.7 299.2 208.3 298.9 207.1 298.6V335.1H223.1C232.8 335.1 239.1 343.2 239.1 351.1C239.1 360.8 232.8 367.1 223.1 367.1H159.1C151.2 367.1 143.1 360.8 143.1 351.1C143.1 343.2 151.2 335.1 159.1 335.1H175.1V298.6C175.7 298.9 175.3 299.2 175 299.5L171.9 302.7C149.1 324.6 114.5 324.6 92.67 302.7C70.8 280.8 70.8 245.4 92.67 223.5L175 141.2zM0 64C0 28.65 28.65 0 64 0H320C355.3 0 384 28.65 384 64V448C384 483.3 355.3 512 320 512H64C28.65 512 0 483.3 0 448V64zM48 64V448C48 456.8 55.16 464 64 464H320C328.8 464 336 456.8 336 448V64C336 55.16 328.8 48 320 48H64C55.16 48 48 55.16 48 64z"
                                            fill="var(--ci-primary-color)">


                                        </path>
                                    </svg>
                                </div>
                                <span
                                    class="flex flex-col items-center justify-center text-center text-xs font-bold text-white lg:text-sm">Blackjack
                                    <span class="text-[10px] font-normal lg:text-xs">Live</span>
                                </span>
                            </a>
                        </li> -->

                        <li class="site-filter-item cursor-pointer hover:opacity-80">
                            <a href="/casino/provider/all/category/roletas"
                                class="flex flex-col items-center justify-center">
                                <div
                                    class="mb-2 flex h-[60px] w-[60px] items-center justify-center rounded-full bg-[var(--ci-primary-opacity-color)]">
                                    <svg width="30" height="30" viewBox="0 0 512 512"
                                        xmlns="http://www.w3.org/2000/svg">
                                        <g clip-path="url(#clip0_14_41)">
                                            <path
                                                d="M224 256C224 238.3 238.3 224 256 224C273.7 224 288 238.3 288 256C288 273.7 273.7 288 256 288C238.3 288 224 273.7 224 256zM512 256C512 397.4 397.4 512 256 512C114.6 512 0 397.4 0 256C0 114.6 114.6 0 256 0C397.4 0 512 114.6 512 256zM256 64C149.1 64 64 149.1 64 256C64 362 149.1 448 256 448C362 448 448 362 448 256C448 149.1 362 64 256 64z"
                                                fill="var(--ci-primary-color)"> </path>
                                        </g>
                                        <defs>
                                            <clipPath id="clip0_14_41">
                                                <rect width="800" height="800" fill="white">

                                                </rect>
                                            </clipPath>
                                        </defs>
                                    </svg>
                                </div>
                                <span
                                    class="flex flex-col items-center justify-center text-center text-xs font-bold text-white lg:text-sm">Roleta
                                    <span class="text-[10px] font-normal lg:text-xs">Live</span></span>
                            </a>
                        </li>

                        <li class="site-filter-item cursor-pointer hover:opacity-80">
                            <a href="games/play/14405/TopCard000000001"
                                class="flex flex-col items-center justify-center">
                                <div
                                    class="mb-2 flex h-[60px] w-[60px] items-center justify-center rounded-full bg-[var(--ci-primary-opacity-color)]">
                                    <svg width="30" height="30" viewBox="0 0 384 512"
                                        xmlns="http://www.w3.org/2000/svg">
                                        <path
                                            d="M175 141.2C184.4 131.8 199.6 131.8 208.1 141.2L291.3 223.5C313.2 245.4 313.2 280.8 291.3 302.7C269.5 324.6 234 324.6 212.1 302.7L208.1 299.5C208.7 299.2 208.3 298.9 207.1 298.6V335.1H223.1C232.8 335.1 239.1 343.2 239.1 351.1C239.1 360.8 232.8 367.1 223.1 367.1H159.1C151.2 367.1 143.1 360.8 143.1 351.1C143.1 343.2 151.2 335.1 159.1 335.1H175.1V298.6C175.7 298.9 175.3 299.2 175 299.5L171.9 302.7C149.1 324.6 114.5 324.6 92.67 302.7C70.8 280.8 70.8 245.4 92.67 223.5L175 141.2zM0 64C0 28.65 28.65 0 64 0H320C355.3 0 384 28.65 384 64V448C384 483.3 355.3 512 320 512H64C28.65 512 0 483.3 0 448V64zM48 64V448C48 456.8 55.16 464 64 464H320C328.8 464 336 456.8 336 448V64C336 55.16 328.8 48 320 48H64C55.16 48 48 55.16 48 64z"
                                            fill="var(--ci-primary-color)">


                                        </path>
                                    </svg>
                                </div>
                                <span
                                    class="flex flex-col items-center justify-center text-center text-xs font-bold text-white lg:text-sm">Futebol
                                    <span class="text-[10px] font-normal lg:text-xs">Studio</span>
                                </span>
                            </a>
                        </li>
                    </ul>
                </div>

                <!-- Favoritos -->
                <div v-if="sortedFeaturedGames.length" class="mt-3">
                    <div class="w-full flex justify-between mb-2">
                        <div class="flex items-center">
                            <h2 class="text-lg" style="color: white">{{ $t('Recomendados') }}</h2>
                            <button @click.prevent="fgCarousel.prev()" 
                                    class="item-game px-2 py-1 rounded-lg text-[12px] ml-2 mr-2 celular-providers-setas">
                                <i class="fa-solid fa-angle-left"></i>
                            </button>
                            <button @click.prevent="fgCarousel.next()" 
                                    class="item-game px-2 py-1 rounded-lg text-[12px] celular-providers-setas">
                                <i class="fa-solid fa-angle-right"></i>
                            </button>
                        </div>
                        <div class="flex"></div>
                    </div>

                    <Carousel class="item-sombra2" ref="fgCarousel" v-bind="settingsGames" 
                            :breakpoints="breakpointsGames" 
                            @init="onCarouselInit(index)" 
                            @slide-start="onSlideStart(index)">
                        <Slide v-if="isLoading" v-for="(i, iloading) in 10" :key="iloading" :index="iloading">
                            <div role="status" 
                                class="w-full flex items-center justify-center h-48 mr-6 max-w-sm bg-gray-300 rounded-lg animate-pulse dark:bg-gray-700 text-4xl">
                                <i class="fa-duotone fa-gamepad-modern"></i>
                            </div>
                        </Slide>

                        <Slide v-if="!isLoading && sortedFeaturedGames.length" 
                            v-for="(game, providerId) in sortedFeaturedGames" 
                            :key="providerId" :index="providerId" class="p-2">
                            <CassinoGameCard :index="providerId" 
                                            :title="game.game_name" 
                                            :cover="game.cover" 
                                            :gamecode="game.game_code" 
                                            :type="game.distribution" 
                                            :game="game" />
                        </Slide>
                    </Carousel>
                </div>

                <!-- Games -->
                <div class="mt-5 ">
                    <ShowProviders v-for="(provider, index) in providers" :provider="provider" :index="index" />
                </div>
                <br>
                <br>
                <br>
                <!-- Provedores -->
                <div>
                    <Carousel v-bind="settings2" :breakpoints="breakpointsRecommended" ref="carouselSubBanner">
                        <Slide v-for="(banner, index) in bannersHome" :key="index">
                            <div class="carousel__item w-full mr-4 max-h-[200px] md:max-h-[200px] p-1 rounded overflow-hidden" style="background-color: var(--navtop-color-dark);"> 
                                <a :href="banner.link" class="w-full h-full rounded">
                                    <!-- Imagem com fit cover para ajustar o tamanho da imagem no contêiner -->
                                    <img :src="`/storage/` + banner.image" alt="banner" class="h-full w-full object-cover">
                                </a>
                            </div>
                        </Slide>
                    </Carousel>
                </div>


            </div>
        </div>
    </BaseLayout>
</template>

<script>
import {
    Carousel,
    Navigation,
    Pagination,
    Slide
} from 'vue3-carousel';
import {
    onMounted,
    ref
} from "vue";

import BaseLayout from "@/Layouts/BaseLayout.vue";
import MakeDeposit from "@/Components/UI/MakeDeposit.vue";
import {
    RouterLink,
    useRoute
} from "vue-router";
import {
    useAuthStore
} from "@/Stores/Auth.js";
import LanguageSelector from "@/Components/UI/LanguageSelector.vue";
import CassinoGameCard from "@/Pages/Cassino/Components/CassinoGameCard.vue";
import HttpApi from "@/Services/HttpApi.js";
import ShowCarousel from "@/Pages/Home/Components/ShowCarousel.vue";
import {
    useSettingStore
} from "@/Stores/SettingStore.js";
import LoadingComponent from "@/Components/UI/LoadingComponent.vue";
import ShowProviders from "@/Pages/Home/Components/ShowProviders.vue";
import {
    searchGameStore
} from "@/Stores/SearchGameStore.js";
import CustomPagination from "@/Components/UI/CustomPagination.vue";

export default {
    props: [],
    components: {
        CustomPagination,
        Pagination,
        ShowProviders,
        LoadingComponent,
        ShowCarousel,
        CassinoGameCard,
        Carousel,
        Navigation,
        Slide,
        LanguageSelector,
        MakeDeposit,
        BaseLayout,
        RouterLink
    },
    data() {
        return {
            isLoading: true,

            /// banners settings
            settings: {
                itemsToShow: 1,
                snapAlign: 'center',
                autoplay: 6000,
                wrapAround: true
            },
            breakpoints: {
                700: {
                    itemsToShow: 1,
                    snapAlign: 'center',
                },
                1024: {
                    itemsToShow: 1,
                    snapAlign: 'center',
                },
            },

            settingsRecommended: {
                itemsToShow: 2,
                snapAlign: 'start',
            },

            settings2: {
                itemsToShow: 4,
                snapAlign: 'center',
                autoplay: 6000,
                wrapAround: true
            },
            breakpointsRecommended: {
                700: {
                    itemsToShow: 5,
                    snapAlign: 'center',
                },
                1024: {
                    itemsToShow: 5,
                    snapAlign: 'start',
                },
            },

            /// banners
            banners: null,
            bannersHome: null,

            settingsGames: {
                itemsToShow: 2.5,
                snapAlign: 'start',
            },
            breakpointsGames: {
                700: {
                    itemsToShow: 3.5,
                    snapAlign: 'center',
                },
                1024: {
                    itemsToShow: 6,
                    snapAlign: 'start',
                },
            },
            settingsImages: {
                itemsToShow: 2,
                snapAlign: 'start',
            },
            providers: null,

            featured_games: null,
            categories: null,
        }
    },
    setup(props) {
        const ckCarouselOriginals = ref(null)
        const fgCarousel = ref(null)

        onMounted(() => {

        });

        return {
            ckCarouselOriginals,
            fgCarousel
        };

    },
    computed: {
        searchGameStore() {
            return searchGameStore();
        },
        userData() {
            const authStore = useAuthStore();
            return authStore.user;
        },
        isAuthenticated() {
            const authStore = useAuthStore();
            return authStore.isAuth;
        },
        setting() {
            const settingStore = useSettingStore();
            return settingStore.setting;
        },
        sortedFeaturedGames() {
            if (this.featured_games && Array.isArray(this.featured_games)) {
                console.log('Featured games before sorting:', this.featured_games);
                return [...this.featured_games].sort((a, b) => (b.views || 0) - (a.views || 0));
            }
            return [];
        }
    },
    mounted() {
        window.scrollTo(0, 0);
        window.addEventListener('scroll', () => {
            const btnScrollTop = document.querySelector('.btn-scroll-top');
            if (window.scrollY > 100) {
                btnScrollTop.classList.add('show-btn-scroll-top');
            } else {
                btnScrollTop.classList.remove('show-btn-scroll-top');
            }
        });
    },
    methods: {
        scrollToTop() {
            window.scrollTo({ top: 0, behavior: 'smooth' });
        },
        getCasinoCategories: async function () {
            const _this = this;
            await HttpApi.get('categories')
                .then(response => {
                    _this.categories = response.data.categories;
                })
                .catch(error => {
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {

                    });
                });
        },
        toggleSearch: function () {
            this.searchGameStore.setSearchGameToogle();
        },
        getBanners: async function () {
            const _this = this;

            try {
                const response = await HttpApi.get('settings/banners');
                const allBanners = response.data.banners;

                _this.banners = allBanners.filter(banner => banner.type === 'carousel');
                _this.bannersHome = allBanners.filter(banner => banner.type === 'home');
            } catch (error) {
                console.error(error);
            } finally {

            }
        },
        getAllGames: async function () {
            const _this = this;
            return await HttpApi.get('games/all')
                .then(async response => {
                    if (response.data !== undefined) {
                        _this.providers = response.data.providers;
                        _this.isLoading = false;
                    }
                })
                .catch(error => {
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {
                        console.log(`${value}`);
                    });
                    _this.isLoading = false;
                });
        },
        getFeaturedGames: async function () {
            const _this = this;
            return await HttpApi.get('featured/games')
                .then(async response => {


                    _this.featured_games = response.data.featured_games;
                    _this.isLoading = false;
                })
                .catch(error => {
                    Object.entries(JSON.parse(error.request.responseText)).forEach(([key, value]) => {
                        console.log(`${value}`);
                    });
                    _this.isLoading = false;
                });
        },
        initializeMethods: async function () {
            await this.getCasinoCategories();
            await this.getBanners();
            await this.getAllGames();
            await this.getFeaturedGames();
        },
        onCarouselInit(index) {

        },
        onSlideStart(index) {

        },

    },
    async created() {
        await this.initializeMethods();
    },
    watch: {


    },
};

// Bloqueia o atalho de teclado para abrir o Console
document.onkeydown = function (event) {
    if (event.keyCode == 123) { // 123 é o código da tecla F12
        return false;
    }
    // Outros códigos de tecla que você deseja bloquear podem ser adicionados aqui
};
// Bloqueia o menu de contexto padrão
document.addEventListener('contextmenu', function (e) {
    e.preventDefault();
});


</script>
