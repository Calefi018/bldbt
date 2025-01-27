<template>
    <div class="flex flex-col sm:flex-row items-center dark:bg-gray-700 w-full rounded-xl p-4 mb-3 h-auto sm:h-[130px]" :key="index">
        <div class="h-auto w-[80px] sm:w-[100px] mr-2 mb-3 sm:mb-0 flex justify-center">
            <div class="pie" :style="`--percentage: ` + (mission.myRoundsPercentage ?? 0)">{{ mission.myRounds }}</div>
        </div>
        <div class="flex flex-col w-full sm:w-auto text-center sm:text-left items-center sm:items-start">
            <h1 class="text-xl sm:text-2xl font-bold mb-1">{{ mission.challenge_name }}</h1>
            <div class="text-xs sm:text-sm text-gray-400 mb-2">
                {{ state.limitCharacters(stripHTML(mission.challenge_description), 80) }}
            </div>
            <h2 class="text-yellow-400 font-extrabold text-xl sm:text-2xl italic">
                {{ state.currencyFormat(parseFloat(mission.challenge_bonus), mission.challenge_currency) }}
            </h2>
        </div>
        <div class="flex justify-center items-center w-full sm:w-[150px] px-3 mt-4 sm:mt-0">
            <button v-if="!mission.haveMission" @click.prevent="acceptMission(mission.id)" class="flex justify-center items-center text-center ui-button-blue mr-3 rounded w-full sm:w-[100px]">
                {{ $t('Accept') }}
            </button>
            <button v-else class="flex justify-center items-center text-center ui-button-black mr-3 rounded w-full sm:w-[100px]">
                {{ $t('Active') }}
            </button>
        </div>
    </div>
</template>



<script>

import HttpApi from "@/Services/HttpApi.js";
import {useToast} from "vue-toastification";

export default {
    props: ['mission', 'index'],
    components: {},
    data() {
        return {
            isLoading: false,
            missions: null,
        }
    },
    setup(props) {


        return {};
    },
    computed: {

    },
    mounted() {

    },
    methods: {
        acceptMission: async function(id) {
            const _this = this;
            const _toast = useToast();

            return await HttpApi.post('missionsusers', { mission_id: id })
                .then(async response =>  {
                    if(response.data.status) {
                        _this.$emit('updateMission');
                        _toast.success(_this.$t('Mission accepted successfully'));
                    }
                })
                .catch(error => {

                });
        },
        stripHTML: function(html) {
            var doc = new DOMParser().parseFromString(html, 'text/html');
            return doc.body.textContent || "";
        },
    },
    created() {

    },
    watch: {

    },
};
</script>

<style scoped>

</style>
