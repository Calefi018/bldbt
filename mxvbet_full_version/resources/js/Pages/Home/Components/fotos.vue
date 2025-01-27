<template>
  <div class="block sm:hidden carousel-container" ref="carouselContainer">
    <div class="slider npm rum build" ref="slider">
      <div class="slide npm rum build" v-for="(image, index) in images" :key="index">
        <a :href="image.href" target="_blank">
          <img :src="image.src" :alt="image.alt" />
          <div class="slide-caption npm rum build">{{ image.caption }}</div>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      startX: 0,
      currentX: 0,
      slideWidth: 320, // Ajuste a largura do slide para exibir duas imagens
      images: [
        { src: 'https://via.placeholder.com/300x200', alt: 'Imagem 1', caption: 'Top 1', href: 'https://example.com/1' },
        { src: 'https://via.placeholder.com/300x200', alt: 'Imagem 2', caption: 'Top 2', href: 'https://example.com/2' },
        { src: 'https://via.placeholder.com/300x200', alt: 'Imagem 3', caption: 'Top 3', href: 'https://example.com/3' },
        { src: 'https://via.placeholder.com/300x200', alt: 'Imagem 4', caption: 'Top 4', href: 'https://example.com/4' }
      ]
    };
  },
  mounted() {
    this.updateSlideWidth();
    window.addEventListener('resize', this.updateSlideWidth);
    this.initializeTouchEvents();
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.updateSlideWidth);
  },
  methods: {
    updateSlideWidth() {
      const containerWidth = this.$refs.carouselContainer.clientWidth;
      // A largura de um slide deve ser a largura do contêiner dividido por 2
      this.slideWidth = containerWidth / 2;
      this.$refs.slider.style.width = `${this.images.length * this.slideWidth}px`;
    },
    initializeTouchEvents() {
      const slider = this.$refs.carouselContainer;

      slider.addEventListener('touchstart', (e) => {
        this.startX = e.touches[0].clientX;
        this.currentX = this.startX;
        this.$refs.slider.style.transition = 'none'; // Desativa a transição durante o arrasto
      }, { passive: true });

      slider.addEventListener('touchmove', (e) => {
        const touch = e.touches[0];
        const deltaX = touch.clientX - this.startX;
        this.currentX = touch.clientX;
        // Remove o translateX e ajusta o scroll
        this.$refs.slider.scrollLeft -= deltaX;
        this.startX = touch.clientX; // Atualiza o ponto de início
        e.preventDefault(); // Previne o comportamento padrão de rolagem
      }, { passive: false });

      slider.addEventListener('touchend', () => {
        const threshold = this.slideWidth / 3;
        const deltaX = this.currentX - this.startX;

        if (Math.abs(deltaX) > threshold) {
          if (deltaX < 0) {
            this.nextSlide();
          } else {
            this.prevSlide();
          }
        }

        // Reativa a transição e ajusta a posição
        this.$refs.slider.style.transition = 'scroll-left 0.3s ease';
        this.$refs.slider.scrollLeft = this.currentIndex * this.slideWidth;
      });
    },
    prevSlide() {
      this.currentIndex = Math.max(0, this.currentIndex - 1);
      this.updateSliderPosition();
    },
    nextSlide() {
      this.currentIndex = Math.min(this.images.length - 1, this.currentIndex + 1);
      this.updateSliderPosition();
    },
    updateSliderPosition() {
      this.$refs.slider.scrollLeft = this.currentIndex * this.slideWidth;
    }
  }
};
</script>

<style scoped>
.carousel-container {
  display: flex;
  align-items: center;
  overflow: hidden;
  position: relative;
  width: 95%;
  max-width: 100%;
  margin: auto;
  cursor: grab;
}

.slider {
  display: flex;
  overflow-x: auto; /* Permite o rolar horizontal */
  scroll-behavior: smooth; /* Transição suave ao rolar */
}

.slide {
  flex: 0 0 20%; /* Exibe duas imagens por vez */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
  overflow: hidden;
  position: relative;
  margin-right:15px;
}

.slide img {
  width: 100%;
  height: auto;
  display: block;
}

.slide-caption {
  text-align: center;
  padding: 3px;
  border-top: 1px solid rgba(0, 0, 0, 0.2); /* Borda fina no topo do texto */
  background: rgba(255, 255, 255, 0.7); /* Fundo translúcido para melhor legibilidade */
}

@media (min-width: 768px) {
  .carousel-container {
    cursor: default;
    touch-action: none; /* Desativa a interação com toque em telas grandes */
  }
}
</style>
