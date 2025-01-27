
<template>
 <!-- <h2 class="text-2xl text-gray-400 width: 2px;">{{ $t(getDayOfWeek()) }}</h2>-->
                <!-- Mission Modal body -->
                <div class="p-4 md:p-5 space-y-4 top-custom">
                    <div class="flex justify-between">
      
                    <div id="tabContentExample">
                        
                        <div
                        class="hidden rounded-lg bg-gray-50 p-2 dark:bg-gray-800"
    id="daily-mission"
    role="tabpanel"
    aria-labelledby="daily-mission-tab"
    style="width: 345px; height: 250px; margin: 0px;">
    <MissionDaily/>
</div>

                        <div
                            class="hidden rounded-lg bg-gray-50 p-4 dark:bg-gray-800"
                            id="weekly-tasks"
                            role="tabpanel"
                            aria-labelledby="weekly-tasks-tab">
                            <MissionWeekly />
                            
                        </div>
                    </div></div></div>
                
   
</template>

<script>
import { initFlowbite, Tabs, Modal } from 'flowbite';
import { onMounted } from "vue";

import { useAuthStore } from "@/Stores/Auth.js";
import { missionStore } from "@/Stores/MissionStore.js";
import MissionDaily from "@/Pages/Home/Components/MissionDaily.vue";
import MissionWeekly from "@/Pages/Home/Components/MissionWeekly.vue";
import pagos from "@/Pages/Home/Components/pagos.vue";


export default {
    props: [],
    components: {
        MissionWeekly,
        MissionDaily,
        pagos
    },
    data() {
        return {
            tabsMission: null,
            modalMission: null,
        }
    },
    setup(props) {

        onMounted(() => {
            initFlowbite();
        });

        return {

        };
    },
    computed: {
        isAuthenticated() {
            const authStore = useAuthStore();
            return authStore.isAuth;
        },
        missionModal() {
            const mission = missionStore()
            return mission.getMissionStatus;
        },
    },
    mounted() {

        /// MISSION MODAL
        const $targetEl = document.getElementById('modalMissionEl');
        const options = {
            placement: 'bottom-right',
            backdrop: 'dynamic',
            backdropClasses: 'bg-black/80 fixed inset-0 z-40 backdrop-blur-md',
            closable: true,
            onHide: () => {

            },
            onShow: () => {

            },
            onToggle: () => {

            },
        };

        const instanceOptions = {
            id: 'modalMissionEl',
            override: true
        };

        this.modalMission = new Modal($targetEl, options, instanceOptions);


        /// MISSION TAB
        const tabsElement = document.getElementById('tabs-mission');
        const tabElements = [
            {
                id: 'profile',
                triggerEl: document.querySelector('#daily-mission-tab'),
                targetEl: document.querySelector('#daily-mission'),
            },
            {
                id: 'dashboard',
                triggerEl: document.querySelector('#weekly-tasks-tab'),
                targetEl: document.querySelector('#weekly-tasks'),
            },
        ];
        const optionsTab = {
            defaultTabId: 'settings',
            activeClasses: 'active-tab text-green-600 hover:text-blue-600 dark:text-green-500 dark:hover:text-green-400 border-green-600 dark:border-green-500',
            inactiveClasses: 'text-gray-500 hover:text-gray-600 dark:text-gray-400 border-gray-100 hover:border-gray-300 dark:border-gray-700 dark:hover:text-gray-300',
            onShow: () => {

            },
        };
        const instanceTabOptions = {
            id: 'tabs-mission',
            override: true
        };

        this.tabsMission = new Tabs(tabsElement, tabElements, optionsTab, instanceTabOptions);
    },
    methods: {
        toggleMissionModal: function() {
            this.modalMission.toggle();
        },
        getDayOfWeek() {
            const daysOfWeek = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];
            const currentDate = new Date();
            const dayOfWeek = daysOfWeek[currentDate.getDay()];
            return dayOfWeek;
        },
    },
    watch: {
        missionModal(newValue, oldValue) {
            this.modalMission.toggle();
        }
    },
};
 
</script>
