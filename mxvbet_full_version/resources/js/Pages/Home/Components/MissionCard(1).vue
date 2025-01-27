<template>
  <!---  <div class="flex dark:bg-gray-700 w-full rounded-xl p-1 mb-1 h-[130px]" :key="index">
        <div class="h-auto w-[180px] mr-2"> --->
        <!---    <div class="pie" :style="`--percentage: `+mission.myRoundsPercentage ?? 0">{{ mission.myRounds }}</div>-->
        
        <div class="flex-col w-full width: 10px;">
             <h1  class="text-2xl font-bold ">{{ mission.challenge_name }}</h1> 
            <h2 style="color: var(--ci-primary-color); font-weight: 800; font-size: 0.5rem; font-style: italic;">{{ state.currencyFormat(parseFloat(mission.challenge_bonus), mission.challenge_currency) }}</h2>

         <div class="flex items-center ">   
         
          <div class="text-sm text-gray-400">Regras : {{ state.limitCharacters(stripHTML(mission.challenge_description), 80) }}</div>
           
        
     </div>
 <div class="flex items-center ">
     <button v-if="!mission.haveMission" @click.prevent="acceptMission(mission.id)" class="flex justify-center items-center text-center ui-button-blue mr-3 rounded " style="backgroundColor: red;  width: 2px; ,height: 4rem; padding: 0 2.55rem;">
                {{ $t('Participar') }}
            </button>
           <button  v-else class="flex justify-center items-center text-center text-sm ui-button-black  rounded" style=" width: 1px; ,height: 1nrem; padding: 0 2.55rem;">
                {{ $t('Participando') }} 
            </button> 
          
            <img src="https://static.bet7k.com/deploy-3843e5556cbefaf26f9f3ca4eaf04084a2181f7b-cb8fad1529a57e0ad511/assets/images/trophy.webp" alt="Loading GIF" style="width: 100px; height: auto;" />
            <pagos/>
 
</div></div>
</template>


<script>

import HttpApi from "@/Services/HttpApi.js";
import {useToast} from "vue-toastification";
import pagos from "@/Pages/Home/Components/pagos.vue";
export default {
    props: ['mission', 'index'],
    components: {
        pagos
    },
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
                        _toast.success(_this.$t('Você aceitou a missão'));
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
