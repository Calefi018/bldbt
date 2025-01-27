<template>
  <div class="time-container">
    <p>{{ currentTime }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentTime: this.formatTime(new Date())
    };
  },
  created() {
    this.startClock();
  },
  methods: {
    formatTime(date) {
      const hours = String(date.getHours()).padStart(2, '0');
      const minutes = String(date.getMinutes()).padStart(2, '0');
      const seconds = String(date.getSeconds()).padStart(2, '0');
      return `${hours}:${minutes}:${seconds}`;
    },
    updateClock() {
      this.currentTime = this.formatTime(new Date());
    },
    startClock() {
      this.updateClock(); // Set initial time
      setInterval(this.updateClock, 1000); // Update every second
    }
  }
}
</script>

<style scoped>
.time-container {
  font-size: 18px;
  font-family: Arial, sans-serif;
}
</style>
