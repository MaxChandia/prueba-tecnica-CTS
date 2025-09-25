<template>
  <div class="slider-container">
    <div 
      class="slider-image" 
      :style="{ backgroundImage: 'url(' + currentImage + ')' }"
    ></div>
    <div class="slider-overlay">
      <h1>¿Quieres vivir una experiencia inolvidable con el amor de tu vida?</h1>
      <p>Este San Valentín, CTS Turismo te invita a celebrar y participar por un viaje soñado a Valdivia</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const images = ref([
  '/photos/Valdivia-1.jpg',
  '/photos/Valdivia-2.jpg',
  '/photos/Valdivia-3.jpg'
]);
const currentIndex = ref(0);
const currentImage = ref(images.value[0]);
let slideInterval = null;

const startSlider = () => {
  slideInterval = setInterval(() => {
    currentIndex.value = (currentIndex.value + 1) % images.value.length;
    currentImage.value = images.value[currentIndex.value];
  }, 4000); 
};

onMounted(() => {
  startSlider();
});

onUnmounted(() => {
  clearInterval(slideInterval);
});
</script>

<style scoped>
.slider-container {
  position: relative;
  width: 100%;
  height: 90vh;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.slider-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  transition: background-image 1s ease-in-out;
}

.slider-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: white;
  padding: 20px;
  box-sizing: border-box;
}

.slider-overlay h1 {
  font-size: 3em;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
}

.slider-overlay p {
  font-size: 1.5em;
  margin-top: 20px;
  text-shadow: 2px 2px 6px rgba(0, 0, 0, 0.9);
  color: #ee930aff;
  font-style: italic;
  
}

@media (max-width: 768px) {
  .slider-overlay h1 {
    font-size: 2em;
  }
  .slider-overlay p {
    font-size: 1em;
  }
}
</style>