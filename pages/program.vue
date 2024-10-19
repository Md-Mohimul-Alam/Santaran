<template>
  <div class="container mt-5">
    <p>All are running successfully by the organization as the part of its journey. Apart from that, Santaran
believes that through these activities our artistic philosophy will become the ‘Yanbriksha’ (alike a
Banyan tree of knowledge) which is rooted to the ground but spreading its branches all over the
sky.</p>

    <div class="row">
      <div
        v-for="(program, index) in programs"
        :key="index"
        class="col-md-6 col-sm-12 mb-4"
        @mouseover="handleMouseOver(index)"
        @mouseleave="handleMouseLeave(index)"
      >
        <div
          class="card"
          :style="{ backgroundImage: `url(${program.image})` }" 
        >
          <div class="card-body">
            <h5 class="card-title" :class="{ animated: animationState[index] || (isMobile && hasAnimatedOnce) }">
              {{ program.name }}
            </h5>
            <p class="card-text" :class="{ animated: animationState[index] || (isMobile && hasAnimatedOnce) }">
              {{ program.description }}
            </p>
            <NuxtLink :to="program.link" class="btn">Learn More</NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  setup() {
    const programs = ref([
      {
        name: "Horith",
        description: "Art of environmental development.",
        link: "/pages/program/horith",
        image: "/horith.jpg", 
      },
      {
        name: "Shikar",
        description: "Development and persistence of folk arts & crafts.",
        link: "/pages/program/shikar",
        image: "/shikar.jpg", 
      },
      {
        name: "Kalpapuri",
        description: "Related to children's art and psychology.",
        link: "/pages/program/kalpapuri",
        image: "/kalpapuri.jpg", 
      },
      {
        name: "Art-Factory",
        description: "An inspiring initiative aimed at young artists.",
        link: "/pages/program/art-factory",
        image: "/art-factory.jpg", 
      },
    ]);

    const animationState = ref(new Array(programs.value.length).fill(false));
    const hasAnimatedOnce = ref(false);
    const isMobile = ref(false);

    const handleMouseOver = (index) => {
      if (!isMobile.value) {
        animationState.value[index] = true;
      }
    };

    const handleMouseLeave = (index) => {
      if (!isMobile.value) {
        animationState.value[index] = false;
      }
    };

    onMounted(() => {
      isMobile.value = window.innerWidth <= 768;
      if (isMobile.value && !hasAnimatedOnce.value) {
        animationState.value.fill(true);
        setTimeout(() => {
          animationState.value.fill(false);
        }, 1500);
        hasAnimatedOnce.value = true;
      }
    });

    return {
      programs,
      animationState,
      handleMouseOver,
      handleMouseLeave,
      hasAnimatedOnce,
      isMobile,
    };
  },
};
</script>

<style scoped>

.container {
  max-width: 1200px;
  min-height: 100vh;
  margin: 0 auto;
  padding: 10px 20px 20px 20px;
  
}

h1 {
  text-align: center;
  margin-bottom: 30px;
  font-size: 2.5rem;
  color: #333;
}

p {
  text-align: center;
  font-size: 1.2rem;
  margin-bottom: 50px;
  color: #666;
}

.row {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 20px;
  height: 100%;
}

.card {
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 20px;
  color: white;
  overflow: hidden;
  transition: transform 0.3s ease, opacity 0.3s ease;
  
}

.card:hover{
  background-color: rgba(0, 0, 0, 0.5);
  background-blend-mode: multiply; 
}

.card:hover::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.2);
  z-index: 1;
}

.card-body {
  position: relative;
  z-index: 2;
}

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

.btn {
  display: inline-block;
  padding: 10px 20px;
  background-color: #007bff;
  color: white;
  text-align: center;
  border-radius: 4px;
  text-decoration: none;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #0056b3;
}

.col-md-6 {
  flex: 0 0 calc(50% - 20px);
}

/* Hover effect specifically for mobile (max-width: 768px) */
@media (max-width: 768px) {
  .col-md-6 {
    flex: 0 0 calc(50% - 10px);
  }

  .card {
    background-color: rgba(0, 0, 0, 0.5); /* Default for mobile */
    opacity: 1; /* Full opacity by default */
  }

  .card:hover {
    opacity: 0.7; /* Decrease opacity on hover */
  }
}

@media (max-width: 576px) {
  .col-md-6 {
    flex: 0 0 100%;
  }

  .card {
    opacity: 1; /* Full opacity by default on small mobile devices */
  }

  .card:hover {
    opacity: 0.7; /* Decrease opacity on hover */
  }
}

.mb-4 {
  margin-bottom: 1.5rem;
}

</style>
