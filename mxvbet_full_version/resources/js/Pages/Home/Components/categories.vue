<template>
   
  <div class="carousel-container"
       @mousedown="startDrag"
       @mouseup="stopDrag"
       @mousemove="onDrag"
       @mouseleave="stopDrag"
       @touchstart="startTouchDrag"
       @touchend="stopDrag"
       @touchmove="onTouchDrag"
       ref="carouselContainer">
    <div class="carousel-wrapper" ref="carouselWrapper">
      <div class="carousel" :style="{ transform: `translateX(-${currentOffset}px)` }">
        <div v-for="(item, index) in items" :key="index" class="carousel-item">
          <a :href="item.href" class="flex items-center" style="align-items: center;">
            <svg height="1em" viewBox="0 0 512 512" width="1em" xmlns="http://www.w3.org/2000/svg"></svg>
            <img :src="item.imgSrc" :alt="item.imgAlt" :title="item.imgTitle" width="20px" height="20px">
            <p class="text-[16px] font-bold" style="font-size: .875rem; font-weight: 700; padding-left: 8px;">{{ item.text1 }}</p>
            <p class="text-[16px] font-bold" style="font-size: .875rem; font-weight: 700; padding-left: 8px;">{{ item.text2 }}</p>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/6cfb1a78-8bb3-4276-9635-7cae424677e3.png', imgAlt: 'Top Jogos', imgTitle: 'Top Jogos', text1: 'Top', text2: 'slot' },
        { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/6cb7a2ad-d9f0-44f4-b825-287b520c12da.png', imgAlt: 'CASUAL', imgTitle: 'CASUAL', text1: 'Ao', text2: 'vivo' },
        { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/3ab1fc7f-b0d5-4952-92a7-87c4ef1e1e02.png', imgAlt: 'ROULETTE', imgTitle: 'ROULETTE', text1: 'Roletas', text2: '' },
        { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/19c3d04f-2d2a-4e63-b183-4dc8dadee03e.png', imgAlt: 'TABLE', imgTitle: 'TABLE', text1: 'Cartas', text2: '' },
         { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/6cfb1a78-8bb3-4276-9635-7cae424677e3.png', imgAlt: 'Top Jogos', imgTitle: 'Top Jogos', text1: 'Top', text2: 'slot' },
        { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/6cb7a2ad-d9f0-44f4-b825-287b520c12da.png', imgAlt: 'CASUAL', imgTitle: 'CASUAL', text1: 'Ao', text2: 'vivo' },
        { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/3ab1fc7f-b0d5-4952-92a7-87c4ef1e1e02.png', imgAlt: 'ROULETTE', imgTitle: 'ROULETTE', text1: 'Roletas', text2: '' },
        { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/19c3d04f-2d2a-4e63-b183-4dc8dadee03e.png', imgAlt: 'TABLE', imgTitle: 'TABLE', text1: 'Cartas', text2: '' },
         { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/6cfb1a78-8bb3-4276-9635-7cae424677e3.png', imgAlt: 'Top Jogos', imgTitle: 'Top Jogos', text1: 'Top', text2: 'slot' },
        { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/6cb7a2ad-d9f0-44f4-b825-287b520c12da.png', imgAlt: 'CASUAL', imgTitle: 'CASUAL', text1: 'Ao', text2: 'vivo' },
        { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/3ab1fc7f-b0d5-4952-92a7-87c4ef1e1e02.png', imgAlt: 'ROULETTE', imgTitle: 'ROULETTE', text1: 'Roletas', text2: '' },
        { href: 'games/play/2890/8357', imgSrc: 'https://ngx-images.s3.us-east-1.amazonaws.com/icons/652137e452a1600026fb2640/19c3d04f-2d2a-4e63-b183-4dc8dadee03e.png', imgAlt: 'TABLE', imgTitle: 'TABLE', text1: 'Cartas', text2: '' },
      ],
      startX: 0,
      currentOffset: 0,
      isDragging: false,
      slideWidth: 100, // Ajuste conforme necessário
      slideMargin: 6, // Ajuste conforme necessário
    };
  },
  mounted() {
    this.startAutoSlide();
    this.adjustCarouselCenter();
    window.addEventListener('resize', this.adjustCarouselCenter);
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.adjustCarouselCenter);
  },
  methods: {
    startDrag(event) {
      this.startX = event.clientX;
      this.isDragging = true;
      event.preventDefault();
    },
    startTouchDrag(event) {
      this.startX = event.touches[0].clientX;
      this.isDragging = true;
    },
    stopDrag() {
      this.isDragging = false;
    },
    onDrag(event) {
      if (!this.isDragging) return;
      const deltaX = event.clientX - this.startX;
      this.startX = event.clientX;

      this.updateOffset(deltaX);
    },
    onTouchDrag(event) {
      if (!this.isDragging) return;
      const deltaX = event.touches[0].clientX - this.startX;
      this.startX = event.touches[0].clientX;

      this.updateOffset(deltaX);
    },
    updateOffset(deltaX) {
      const newOffset = Math.max(0, Math.min(this.currentOffset - deltaX, this.getMaxOffset()));
      this.currentOffset = newOffset;
    },
    
    moveSlide(direction) {
      const newOffset = Math.max(0, Math.min(this.currentOffset + direction * (this.slideWidth + this.slideMargin), this.getMaxOffset()));
      this.currentOffset = newOffset;
    },
    getMaxOffset() {
      const carouselWrapperWidth = this.$refs.carouselWrapper.clientWidth;
      const carouselWidth = this.items.length * (this.slideWidth + this.slideMargin);
      return Math.max(0, carouselWidth - carouselWrapperWidth);
    },
    adjustCarouselCenter() {
      const wrapper = this.$refs.carouselWrapper;
      const container = this.$refs.carouselContainer;
      const wrapperWidth = wrapper.scrollWidth;
      const containerWidth = container.clientWidth;
      const centerOffset = Math.max(0, (containerWidth - wrapperWidth) / 2);
      wrapper.style.marginLeft = `${centerOffset}px`;
    },
  },
};
</script>

<style scoped>
.carousel-container {
  position: relative;
  width: 100%;
  overflow: hidden;
  cursor: grab;
  display: flex;
  justify-content: center; /* Centraliza o carrossel horizontalmente */
}

.carousel-wrapper {
  display: flex;
  overflow: hidden;
  width: 100%;
  border-radius: 4px; /* Ajusta o raio das bordas em telas menores, se necessário */
  background: linear-gradient(to right, #6522a8,#6522a8);
 
}

.carousel {
  display: flex;
  transition: transform 0.3s ease;
  
   
}

.carousel-item {
  min-width: 110px; /* Ajuste conforme necessário */
 justify-content: center;
  margin-right: 6px; /* Espaço entre itens */
   justify-content: center; 
   
}

.carousel-container:active {
  cursor: grabbing;
  justify-content: center; 
}
.degrade {
  background: linear-gradient(to right, #6522a8,#6522a8,#0a0705,#0a0705,#0a0705,#0a0705);
 
}

</style>