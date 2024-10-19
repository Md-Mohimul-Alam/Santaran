<template>
    <div class="carousel-container">
      <div class="carousel">
        <div class="carousel-images">
          <div
            v-for="(image, index) in images"
            :key="index"
            :class="{ active: currentIndex === index }"
            class="carousel-slide"
            :style="{ backgroundImage: `url(${image.src})` }"
          >
            <!-- Dark overlay that fades in after the image is visible -->
            <div v-if="currentIndex === index" class="dark-overlay"></div>
  
            <!-- Text overlay that fades in after the dark overlay -->
            <div v-if="currentIndex === index" class="text-overlay">
              <h1>{{ image.title }}</h1>
              <p>{{ image.description }}</p>
            </div>
          </div>
        </div>
  
        <!-- Previous and Next Buttons -->
        <button class="prev" @click="prevSlide">&lt;</button>
        <button class="next" @click="nextSlide">&gt;</button>
  
        <!-- Progress bar -->
        <div class="progress-bar">
          <span class="progress" :style="{ width: progressWidth + '%' }"></span>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onBeforeUnmount } from 'vue';
  
  // Define images for the carousel
  const images = ref([
    { src: '/about_back1.jpg', title: 'Santaran', description: 'Art for Dignifying Life.' },
    { src: '/about_back.jpg', title: 'Santaran', description: 'Santaran, meaning "swimming" in Bengali, is a nonprofit multidisciplinary artist-run organization founded in 1998 in Chittagong, Bangladesh. Officially registered in 2008, Santaran promotes local art, culture, Indigenous wisdom, and human ecology. With a mission to inspire artistic expression rooted in local heritage, it guides communities to embrace art as a powerful medium for enriched living and spiritual connection.' },
    { src: '/Horith.jpg', title: 'Horith', description: 'A beautiful landscape view.' },
    { src: '/shikar.jpg', title: 'Shikar', description: 'The magnificent Shikar in nature.' },
    { src: '/Kalpapuri.jpg', title: 'Kalpapuri', description: 'Kalpapuri – An enchanted place.' },
  ]);
  
  const currentIndex = ref(0);
  const progressWidth = ref(0);
  const slideDuration = 10000; // Duration for each slide (10 seconds)
  const progressInterval = 100; // Interval to update the progress bar (100ms)
  
  // Function to go to the next slide
  const nextSlide = () => {
    currentIndex.value = (currentIndex.value + 1) % images.value.length;
    resetProgress();
  };
  
  // Function to go to the previous slide
  const prevSlide = () => {
    currentIndex.value = (currentIndex.value - 1 + images.value.length) % images.value.length;
    resetProgress();
  };
  
  // Function to reset and start the progress bar
  const resetProgress = () => {
    progressWidth.value = 0; // Reset the progress bar to 0
  };
  
  // Progress updater for smooth transitions
  const updateProgress = () => {
    progressWidth.value += (100 / (slideDuration / progressInterval)); // Increment progress based on time
    if (progressWidth.value >= 100) {
      nextSlide(); // Go to the next slide when progress reaches 100%
    }
  };
  
  // Auto slide change and progress update
  let interval;
  let progressUpdater;
  onMounted(() => {
    interval = setInterval(nextSlide, slideDuration); // Change slide every 10 seconds
    progressUpdater = setInterval(updateProgress, progressInterval); // Update progress bar every 100ms
  });
  
  onBeforeUnmount(() => {
    clearInterval(interval); // Clear slide interval
    clearInterval(progressUpdater); // Clear progress bar updater interval
  });
  </script>
  
  <style scoped>

.card-title {
  font-size: 1.5rem;
  color: #00e676;
  border-bottom: 1px solid #ef6c00;
  margin-bottom: 10px;
  opacity: 0;
  transform: translateY(-10px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.card-text {
  font-size: 1rem;
  color: #fdd835;
  margin-bottom: 20px;
  opacity: 0;
  transform: translateY(-10px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.card-title.animated {
  opacity: 1;
  transform: translateX(-30%);
}

.card-text.animated {
  opacity: 1;
  transform: translateY(0);  
}



/* Full page carousel */
.carousel-container {
  position: relative;
  width: 100vw;
  height: 93vh;
  overflow: hidden;
}
.carousel {
  width: 100%;
  height: 100%;
}

.carousel-images {
  display: flex;
  height: 100%;
}

.carousel-slide {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  display: none;
  opacity: 0;
  position: relative;
  transition: opacity 1s ease-in-out;
}

.carousel-slide.active {
  display: block;
  opacity: 1;
}

.dark-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0);
  transition: background-color 1s ease-in-out 1s;
}

.carousel-slide.active .dark-overlay {
  background-color: rgba(0, 0, 0, 0.5);
}

/* Responsive Text Overlay */
.text-overlay {
  position: absolute;
  bottom: 10%;
  left: 50%;
  transform: translateX(-50%);
  color: white;
  text-align: center;
  text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.7);
  opacity: 0;
  animation: fadeInText 1s ease forwards 2s;
  z-index: 2;
}

/* Responsive Typography using clamp */
.text-overlay h1 {
  font-size: clamp(2rem, 5vw, 3rem); /* Responsive heading */
  color: white;
}

.text-overlay p {
  font-size: clamp(1rem, 2.5vw, 1.5rem); /* Responsive paragraph */
}

@keyframes fadeInText {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Previous and Next buttons */
button.prev,
button.next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: transparent;
  border: none;
  padding: 15px;
  cursor: pointer;
  border-radius: 50%;
  font-size: clamp(1.5rem, 3vw, 2.5rem); /* Responsive button size */
  z-index: 3;
}

button.prev {
  left: 10px;
}

button.next {
  right: 10px;
}

/* Progress bar */
.progress-bar {
  height: 4px;
  width: 100%;
  background-color: rgba(255, 255, 255, 0.2);
  position: absolute;
  bottom: 0;
  left: 0;
  border-radius: 2px;
}

.progress {
  display: block;
  height: 100%;
  background-color: #2992dc;
  transition: width 0.5s ease;
}

/* Media Queries for additional fine-tuning */
@media (max-width: 768px) {
  .text-overlay h1 {
    font-size: 2rem; /* Smaller text for smaller screens */
  }

  .text-overlay p {
    font-size: 1rem;
  }

  button.prev,
  button.next {
    padding: 10px;
    font-size: 1.5rem; /* Smaller buttons for mobile */
  }
}

@media (max-width: 480px) {
  .text-overlay h1 {
    font-size: 1.5rem; /* Even smaller heading for mobile */
  }

  .text-overlay p {
    font-size: 0.9rem;
  }

  button.prev,
  button.next {
    padding: 8px;
    font-size: 1.2rem;
  }
}
</style>
