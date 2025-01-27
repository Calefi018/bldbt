<template>
  <ul class="custom-bg-color flex items-start justify-between gap-3 overflow-y-scroll text-white">
   
                  
                       <div class=" block sm:hidden cursor-pointer w-full margin-search" style="margin-bottom: 0px;">
                    <div class="flex block sm:hidden">
                        <div class="block sm:hidden relative w-full w-[50px] h-[50px]">
                            <button @click="toggleSearch" type="submit" class="absolute top-0 start-0 h-full p-2.5 text-sm font-medium text-white rounded-e-lg">
                                <svg id="svg-lupa" data-v-49f1cded="" height="14px" viewBox="0 0 512 512" width="14px" xmlns="http://www.w3.org/2000/svg" class=" block sm:hidden text-texts w-5 p-0 m-0" style="width: 20px; height: 20px;"><path d="M500.3 443.7l-119.7-119.7c-15.03 22.3-34.26 41.54-56.57 56.57l119.7 119.7c15.62 15.62 40.95 15.62 56.57 0C515.9 484.7 515.9 459.3 500.3 443.7z" fill="currentColor"></path><path d="M207.1 0C93.12 0-.0002 93.13-.0002 208S93.12 416 207.1 416s208-93.13 208-208S322.9 0 207.1 0zM207.1 336c-70.58 0-128-57.42-128-128c0-70.58 57.42-128 128-128s128 57.42 128 128C335.1 278.6 278.6 336 207.1 336z" fill="currentColor" opacity="0.4"></path></svg>
                                <span class="sr-only">Pesquise</span>
                            </button>
                            <input style="w-full w-[50px] h-[50px] background-color: #323637; color: white;" class="w-[50px] h-[50px] w-full  placeholder-search p-0 lg:p-0 search-mobile" @click.prevent="toggleSearch"  type="search"
                                   readonly
                                   placeholder="Pesquise um nome de jogo." required>

                           </div>
                    </div> </div> </ul>
</template>

