<style>
@media(max-width:600px) {
    .celular-providers-setas {
        display: none;
    }
}
</style>

<template>
    <div :key="index" class="game-list flex flex-col relative ">
        <div class="w-full flex justify-between">
            <div class="flex items-center">
                <h2 class="text-lg" style="color: white">{{ $t(provider.name) }}</h2>
                <button @click.prevent="ckCarousel.prev()"
                    class="item-game px-2 py-1 rounded-lg text-[12px] ml-2 mr-2 celular-providers-setas">
                    <i class="fa-solid fa-angle-left"></i>
                </button>
                <button @click.prevent="ckCarousel.next()"
                    class="item-game px-2 py-1 rounded-lg text-[12px] celular-providers-setas">
                    <i class="fa-solid fa-angle-right"></i>
                </button>
            </div>
            <div class="flex items-center ">
                <RouterLink :to="{ name: 'casinosAll', params: { provider: provider.id, category: 'all' } }" class="">
                    <p
                        style="background-color: var(--ci-primary-opacity-color);color: var(--ci-primary-color);font-size: 10px;padding: 0px 5px;border-radius: 10px;">
                        Ver todos</p>
                </RouterLink>
            </div>
        </div>

        <Carousel class="item-sombra2" ref="ckCarousel" v-bind="settingsGames" :breakpoints="breakpointsGames"
            @init="onCarouselInit(index)" @slide-start="onSlideStart(index)">
            <Slide v-if="isLoading" v-for="(i, iloading) in 10" :key="iloading" :index="iloading">
                <div role="status"
                    class="w-full flex items-center justify-center h-48 mr-6 max-w-sm bg-gray-300 rounded-lg animate-pulse dark:bg-gray-700 text-4xl">
                    <i class="fa-duotone fa-gamepad-modern"></i>
                </div>
            </Slide>

            <Slide v-if="!isLoading && sortedGames.length" v-for="(game, providerId) in sortedGames" :key="providerId" :index="providerId"
                class="p-2">
                <CassinoGameCard :index="providerId" :title="game.game_name" :cover="game.cover"
                    :gamecode="game.game_code" :type="game.distribution" :game="game" />
            </Slide>
        </Carousel>
    </div>
</template>

<script>
import { Carousel, Navigation, Slide } from 'vue3-carousel';
import { onMounted, ref, computed } from "vue";
import CassinoGameCard from "@/Pages/Cassino/Components/CassinoGameCard.vue";

export default {
    props: ['provider', 'index'],
    components: { CassinoGameCard, Carousel, Navigation, Slide },
    data() {
        return {
            isLoading: false,
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
        }
    },
    setup(props) {
        const ckCarousel = ref(null);

        onMounted(() => {

        });

        return {
            ckCarousel
        };
    },
    computed: {
        sortedGames() {
            if (this.provider && this.provider.games && Array.isArray(this.provider.games)) {
                console.log('Games before sorting:', this.provider.games);
                return [...this.provider.games].sort((a, b) => (b.views || 0) - (a.views || 0));
            }
            return [];
        }
    },
    methods: {
        onCarouselInit(index) {

        },
        onSlideStart(index) {

        },
    },
};
</script>

<style scoped></style>
