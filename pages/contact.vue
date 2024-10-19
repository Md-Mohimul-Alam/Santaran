<template>
  <section class="contact-section">
    <div class="container">
      <div class="map-section">
        <iframe 
            width="100%" 
            height="100%" 
            class="map-frame" 
            frameborder="0" 
            title="map"
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3687.7451395911576!2d91.8143185747607!3d22.322520857858227!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x30acdf79fb45d755%3A0xeba3688b4edf6eb2!2sSantaran%20Art%20Organisation!5e0!3m2!1sen!2sbd!4v1697653678202!5m2!1sen!2sbd"
            allowfullscreen
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade">
          </iframe>

          <div class="info-box">
          <div class="address-box">
            <h2>ADDRESS</h2>
            <p>91, Amir Hossain Dovash Road, Chattogram, 4100, Bangladesh.</p>
          </div>
          <div class="contact-box">
            <h2>EMAIL - </h2>
            <a href="mailto:santaranartorg@gmail.com">santaranartorg@gmail.com</a>
            <h2>PHONE</h2>
            <p>+8801852367274</p>
          </div>
        </div>
      </div>
      <div class="feedback-section">
        <h2>Feedback</h2>
        <p>Post-ironic portland shabby chic echo park, banjo fashion axe</p>
        <form>
          <div class="form-group">
            <label for="name">Name</label>
            <input type="text" id="name" name="name">
          </div>
          <div class="form-group">
            <label for="email">Email</label>
            <input type="email" id="email" name="email">
          </div>
          <div class="form-group">
            <label for="message">Message</label>
            <textarea id="message" name="message"></textarea>
          </div>
          <button type="submit">Submit</button>
        </form>
      </div>
    </div>
  </section>
</template>
<style scoped>
 * {
   top: 0;
   left: 0;
   right: 0;
   bottom: 0;
 }

.contact-section {
  backdrop-filter: blur(15px);
  background: rgba(255, 255, 255, 0.2);
  display: flex;
  justify-content: center;
  padding: 24px;
  padding-bottom: 240px;
  background-image: url('contact.jpg'); 
   background-size: cover; 
   background-position: center; 
   background-repeat: no-repeat; 
   background-color: rgba(0, 0, 0, 0.7); 
}

.container {
  display: flex;
  flex-wrap: nowrap;
  width: 100%;
  max-width: 1200px;
  padding-top: 100px;
}

.map-section {
  flex: 2;
  position: relative;
  background-color: #f0f0f0;
  padding: 16px;
  border-radius: 8px;
  margin-right: 24px;
  overflow: hidden;
}

.map-frame {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  filter: grayscale(1) contrast(1.2) opacity(0.4);
}

.info-box {
  top: 300px;
  right: 35px;
  position: relative;
  background-color: white;
  padding: 16px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  display: flex;
  justify-content: space-between;
  width: 100%;
}

.address-box,
.contact-box {
  width: 48%;
}

h2 {
  font-size: 12px;
  font-weight: bold;
  color: #333;
  margin-bottom: 8px;
}

p,
a {
  font-size: 14px;
  color: #555;
}

a {
  text-decoration: none;
  color: #1a73e8;
}

.feedback-section {
  flex: 1;
  background-color: white;
  padding: 24px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.feedback-section h2 {
  font-size: 18px;
  margin-bottom: 16px;
  color: #333;
}

.feedback-section p {
  font-size: 14px;
  margin-bottom: 16px;
  color: #777;
}

.form-group {
  margin-bottom: 16px;
}

.form-group label {
  display: block;
  font-size: 14px;
  margin-bottom: 8px;
  color: #333;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 8px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.form-group textarea {
  height: 100px;
  resize: none;
}

button {
  background-color: #1a73e8;
  color: white;
  border: none;
  padding: 12px 24px;
  font-size: 16px;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #1664c1;
}

/* Responsive Design */
@media (max-width: 992px) {
  .container {
    flex-wrap: wrap !important;
  }

  .map-section {
    flex: 1;
    margin-right: 0;
    margin-bottom: 24px;
  }

  .feedback-section {
    flex: 1;
    margin-top: 16px;
  }

  .info-box {
    flex-direction: column;
    top: 250px;
    padding: 12px;
  }

  .address-box,
  .contact-box {
    width: 100%;
    margin-bottom: 16px;
  }

  h2 {
    font-size: 14px;
  }

  p,
  a {
    font-size: 12px;
  }
}

@media (max-width: 768px) {
  .contact-section {
    padding: 16px;
  }

  .map-section {
    padding: 12px;
  }

  .feedback-section {
    padding: 16px;
  }

  .info-box {
    top: 220px;
  }
}

@media (max-width: 576px) {
  .container {
    flex-direction: column;
    padding-bottom: 50px !important;
  }

  .map-section,
  .feedback-section {
    width: 100%;
    margin-right: 0;
    margin-bottom: 16px;
  }

  .map-frame {
    height: 300px;
  }

  .info-box {
    padding: 10px;
  }

  h2 {
    font-size: 16px;
  }

  p,
  a {
    font-size: 14px;
  }

  .form-group input,
  .form-group textarea {
    font-size: 12px;
  }

  button {
    width: 100%;
    padding: 10px;
    font-size: 14px;
  }
}
</style>
