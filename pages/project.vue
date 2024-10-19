<template>
  <div class="container mt-5">
    <h1>Our Projects</h1>
    <p>Explore the initiatives we are working on at Santaran!</p>

    <div class="row">
      <div
        v-for="(project, index) in projects"
        :key="index"
        class="col-md-6 col-sm-12 mb-4"
        @mouseover="handleMouseOver(index)"
        @mouseleave="handleMouseLeave(index)"
      >
        <div class="card">
          <div class="card-body">
            <h5 class="card-title" :class="{ animated: animationState[index] || (isMobile && hasAnimatedOnce) }">
              {{ project.name }}
            </h5>
            <p class="card-text" :class="{ animated: animationState[index] || (isMobile && hasAnimatedOnce) }">
              {{ project.description }}
            </p>
            <NuxtLink :to="project.link" class="btn">Learn More</NuxtLink>
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
    const projects = ref([
      {
        name: "Yearly Outcome",
        description: "Overview of the annual outcomes of our projects.",
        link: "/pages/project/yearly-outcome",
      },
      {
        name: "Multidisciplinary Art Show",
        description: "An exhibition showcasing various art forms.",
        link: "/pages/project/multidisciplinary-art-show",
      },
      {
        name: "Art Exchange ",
        description: "Collaborative art projects with local and international artists.",
        link: "/pages/project/art-exchange",
      },
      {
        name: "Art Workshop ",
        description: "Workshops focused on artistic skills for participants.",
        link: "/pages/project/art-workshop",
      },
      {
        name: "Research Program",
        description: "Programs aimed at researching art and culture.",
        link: "/pages/project/research-program",
      },
      {
        name: "Seminar & Presentation",
        description: "Presentations on various topics in art and culture.",
        link: "/pages/project/seminar-presentation",
      },
      {
        name: "Publication",
        description: "Publications related to art research and findings.",
        link: "/pages/project/publication",
      },
    ]);

    const animationState = ref(new Array(projects.value.length).fill(false));
    const hasAnimatedOnce = ref(false); // Track if animation has occurred on mobile
    const isMobile = ref(false); // Check if the user is on mobile

    const handleMouseOver = (index) => {
      if (!isMobile.value) { // Animate on hover only for desktop
        animationState.value[index] = true; // Set animation state on hover
      }
    };

    const handleMouseLeave = (index) => {
      if (!isMobile.value) { // Reset animation on mouse leave only for desktop
        animationState.value[index] = false; // Reset animation state on mouse leave
      }
    };

    onMounted(() => {
      // Check if the user is on mobile
      isMobile.value = window.innerWidth <= 768;

      // Trigger animation for mobile devices only once after refresh
      if (isMobile.value && !hasAnimatedOnce.value) {
        // Trigger animation once for each card
        animationState.value.fill(true); // Set all cards to animated
        setTimeout(() => {
          animationState.value.fill(false); // Reset after animation
        }, 1500); // Duration to match animation
        hasAnimatedOnce.value = true; // Mark as animated
      }
    });

    return {
      projects,
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
  margin: 0 auto;
  padding: 20px;
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

/* Flexbox grid for arranging the cards */
.row {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 20px; /* Add 20px space between cards */
}

/* Styling for individual cards */
.card {
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 20px;
  overflow: hidden;
  transition: transform 0.3s ease;
}

.card-title {
  font-size: 1.5rem;
  color: #007bff;
  margin-bottom: 10px;
  opacity: 0; /* Initially hidden */
  transform: translateY(-10px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.card-text {
  font-size: 1rem;
  color: #555;
  margin-bottom: 20px;
  opacity: 0; /* Initially hidden */
  transform: translateY(-10px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}
.card-title.animated
{
  opacity: 1; /* Make visible */
  transform: translateX(-20%); /* Slide in */
}

.card-text.animated {
  opacity: 1; /* Make visible */
  transform: translateY(0); /* Slide in */
}

/* Button/link styling */
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

/* Responsive styles */
.col-md-6 {
  flex: 0 0 calc(50% - 20px); /* Two cards per row on medium and larger screens with 20px gap */
}

@media (max-width: 768px) {
  .col-md-6 {
    flex: 0 0 calc(50% - 10px); /* Two cards per row for tablets, smaller gap */
  }
}

@media (max-width: 576px) {
  .col-md-6 {
    flex: 0 0 100%; /* One card per row for mobile */
  }
}

.mb-4 {
  margin-bottom: 1.5rem; /* Add margin to the bottom of each card */
}
</style>
