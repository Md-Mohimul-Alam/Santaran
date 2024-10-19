<template>
  <div class="about">
    <div class="about-container">
      <h1 class="title">About Us</h1>
      <p>
        “Art for Dignifying Life” is the vision of Santaran Art Organization. Santaran means swimming, it is Bengali words. 
        As a group of artists, Santaran has been continuing its journey since 1998. In 2008, it got registration under 
        the Ministry of Social Welfare, People’s Republic of Bangladesh as ‘Santaran Art Organization’, a nonprofit 
        multidisciplinary artist-run organization. Santaran Art Organization is continuing its journey from Chittagong, 
        Bangladesh with the hope and mission to shape the artistic values regarding local reality, Indigenous knowledge, 
        human ecology, art & culture, mythology & spirituality of local people, and environment in a more defined artistic way. 
        Santaran is trying to guide people to acquire art as the strongest medium for their better living.
      </p>
    </div>
  </div>
</template>

<style scoped>
 * {
   top: 0;
   left: 0;
   right: 0;
   bottom: 0;
 }

 .about {
  top: 0;
   left: 0;
   right: 0;
   bottom: 0;
   object-fit: fill;
   background-image: url('about.jpg'); /* Ensure the image path is correct */
   background-size: cover; /* Ensures the image covers the entire background */
   background-position: center; /* Keeps the image centered */
   background-repeat: no-repeat; /* Prevents the image from repeating */
   background-color: rgba(0, 0, 0, 0.7); /* Dark overlay on background image */
  position: relative;
  padding: 100px 0px;
  padding-bottom: 200px;
  animation: grow 2s;
  border-radius: 10px; /* Rounded corners for smooth look */
  background-color: rgba(182, 182, 182, 0.1); /* Slight background overlay */
  transition: color 0.3s ease, background-color 0.3s ease, opacity 0.3s ease;
}

.about:hover {
  box-shadow: 0px 0px 40px rgba(255, 255, 255, 0.7); /* Stronger glow on hover */
  transition: box-shadow 0.5s ease-in-out; /* Smooth transition */
}

.about-container {
  backdrop-filter: blur(15px);
  background: rgba(255, 255, 255, 0.2);
  box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.3); /* Glowing effect */
  position: relative; 
  max-width: 900px;
  margin: 0 auto;
  padding: 40px;
  border-radius: 10px; 
  opacity: 0; /* Initially hidden */
  transform: translateY(50px); /* Slide-up effect */
  transition: opacity 1.5s ease, transform 1.5s ease; 
}

.about-container.show {
  opacity: 1;
  transform: translateY(0); /* Show element when .show is applied */
}

.title {
  font-family: Raleway;
  background: transparent;
  color: #ffffff;
  font-size: 2.5rem;
  text-align: center;
  margin-bottom: 20px;
  opacity: 0; /* Initially hidden */
  transform: translateY(50px); 
  transition: opacity 1.5s ease, transform 1.5s ease;
}

.title.show {
  opacity: 1;
  transform: translateY(0); 
}

p {
  font-size: 1.4rem;
  background: transparent;
  color: #ffffff;
  line-height: 1.8;
  text-align: justify;
  margin-bottom: 20px;
  font-family: 'Georgia', serif;
  opacity: 0; /* Initially hidden */
  transform: translateY(50px);
  transition: opacity 1.5s ease, transform 1.5s ease;
}

p.show {
  opacity: 1;
  transform: translateY(0);
}

/* Responsive adjustments for tablets */
@media (max-width: 768px) {
  .about-container {
    padding: 20px;
  }
  p {
    font-size: 1rem;
  }
}

/* Responsive adjustments for mobile */
@media (max-width: 480px) {
  .about-container {
    padding: 15px;
  }
  p {
    font-size: 0.9rem;
  }
}
</style>

<script>
export default {
  mounted() {
    // Apply the "show" class to both the title and paragraph after the page is loaded
    setTimeout(() => {
      const aboutContainer = document.querySelector('.about-container');
      const title = document.querySelector('.title');
      const paragraph = document.querySelector('p');

      // Add 'show' class to make elements visible with animation
      aboutContainer.classList.add('show');
      title.classList.add('show');
      paragraph.classList.add('show');
    }, 500); // 0.5 seconds delay
  }
}
</script>
