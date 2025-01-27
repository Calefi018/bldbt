<template>
    <BaseLayout>
        <LoadingComponent :isLoading="isLoading">
            <div class="text-center">
                <span>Carregando os jogos</span>
            </div>
        </LoadingComponent>

        <div v-if="!isLoading" class=" mx-auto">
            <div class="px-4">
                <HeaderComponent>
                    <template #header>
                       
                    </template>

                </HeaderComponent>

                <form class="sm:max-w-[1110px] lg:max-w-[1110px] mx-auto w-full mb-[15px] mt-[30px]">
                 
                    <div class="relative flex">
                        
                    </div>
                    <div class="flex start mx-auto items-center">
                    
                       
                        
                              <a style="margin-right: 10px;margin-bottom: 35px;" href="/"><svg height="1em" viewBox="0 0 448 512" width="1em" xmlns="http://www.w3.org/2000/svg"><path d="M9.4 233.4c-12.5 12.5-12.5 32.8 0 45.3l160 160c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3L109.2 288 416 288c17.7 0 32-14.3 32-32s-14.3-32-32-32l-306.7 0L214.6 118.6c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0l-160 160z" fill="currentColor"></path></svg></a> <p class="text-2xl flex items-center justify-center" style="margin-bottom: 35px;font-size: 14px;font-weight: bold;padding-right: 5px;">{{ $t('Todos') }} {{ games?.total ?? 0 }} {{ $t('jogos da categoria.') }}<strong style="font-size: 13px;padding-left: 5px;"> </strong></p>
                   </div>
                
                   <input style="background-color: #202223;padding: 0;padding-left: 15px;padding-top: 5px;padding-bottom: 5px;border-radius: 3px;font-size: 12px;" v-model="searchTerm" @input="searchGames" type="search" id="search"
                               class="block relative w-full"
                               :placeholder="$t('Pesquisar um jogo...')"
                               required>
                </form>

                <div v-if="games && games?.total > 0">
                    <div class="relative w-full sm:max-w-[690px] lg:max-w-[1110px] mx-auto w-full">
                        <div class="grid grid-cols-3 md:grid-cols-6 gap-4 mb-5">
                            <CassinoGameCard
                                v-for="(game, index) in games.data"
                                :index="index"
                                :title="game.game_name"
                                :cover="game.cover"
                                :gamecode="game.game_code"
                                :type="game.distribution"
                                :game="game"
                            />
                        </div>
                    </div>

                    <div class="mt-[50px] relative sm:max-w-[690px] lg:max-w-[1110px] mx-auto w-full">
                        <CustomPagination :data="games" @pagination-change-page="getGameData"/>
                        
                    </div>
                    
                </div>
                <div v-else class="empty-data flex flex-col justify-center items-center text-center mt-[50px] mb-[30px] sm:max-w-[690px] lg:max-w-[1110px] mx-auto w-full">
                    <div class="flex justify-center p-2 w-full" style="background-color: #383028;border-radius: 5px;">
                    <h3 style="color: #FF9F43;font-size: .75rem;">{{ $t('No data to show') }}</h3>
                </div>
                </div>
            </div>
        </div>
    </BaseLayout>
</template>


<script>

import BaseLayout from "@/Layouts/BaseLayout.vue";
import HttpApi from "@/Services/HttpApi.js";
import CassinoGameCard from "@/Pages/Cassino/Components/CassinoGameCard.vue";
import CustomPagination from "@/Components/UI/CustomPagination.vue";
import {useRoute, useRouter} from "vue-router";
import {computed, ref, watch} from "vue";
import LoadingComponent from "@/Components/UI/LoadingComponent.vue";
import HeaderComponent from "@/Components/UI/HeaderComponent.vue";

export default {
    props: [],
    components: {HeaderComponent, LoadingComponent, CustomPagination, CassinoGameCard, BaseLayout},
    data() {
        return {
            isLoading: false,
            games: null,
            searchTerm: '',
            provider: null,
            category: null,
        }
    },
    setup(props) {
        const route = useRoute();

        watch(() => route.params.provider, (newProvider, oldProvider) => {

        });

        return {
            route
        };
    },
    computed: {},
    mounted() {
        window.scrollTo(0, 0);
    },
    beforeUnmount() {},
    methods: {
        searchGames: async function () {
            const _this = this;
            if (_this.searchTerm.length > 2) {
                await _this.getGameData(1,  false);
            }else{
                await _this.getGameData(1,  false);
            }
        },
        getGameData: async function (page = 1, loading = true) {
            const _this = this;
            _this.isLoading = loading;
            const provider = _this.route.params.provider;
            const category = _this.route.params.category;

            this.provider = provider;
            this.category = category;

            await HttpApi.get('/casinos/games?page=' + page + '&searchTerm=' + _this.searchTerm+'&category='+_this.category+'&provider='+_this.provider)
                .then(response => {
                    _this.games = response.data.games;
                    _this.isLoading = false;
                })
                .catch(error => {
                    _this.isLoading = false;
                });
        },
    },
   async created() {

        await this.getGameData(1,  false);
    },
    watch: {
        'route.params.provider'(newGame, oldGame) {
            this.getGameData(1,  true);
        },
        'route.params.category'(newGame, oldGame) {
            this.getGameData(1,  true);
        }
    },
};
</script>

<style scoped>

</style>
