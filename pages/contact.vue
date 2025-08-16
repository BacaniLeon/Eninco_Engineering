<template>
    <BackToTop/>
    <div class="contact_intro_section">
      <Navigation/>
      <div class="contact_intro_section_title">
        <h1>CONTACT US</h1>
      </div>
    </div>

    <div class="our_branches">
        <h4>Our Branches</h4>
        <h2>Contact Details</h2>
    </div>

    <div class="head_office_and_map">
      <div class="head_office">
        <h2>Croatia Head Office & Production Factory</h2>
        <h4>Address:</h4>
        <p>Draganići 14</p>
        <p>47 201</p>
        <p>Draganić, Croatia</p>
        <h4>Phone:</h4>
        <p>+385 99 195 30 86</p>
        <h4>Email:</h4>
        <p>info@eninco-engineering.com</p>
      </div>
      <div class="map">
        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2791.7212437371745!2d15.595649712476092!3d45.59614822450369!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x47643be2819b0eb5%3A0x69e7b9be9b549828!2sEninco%20Engineering%20d.o.o.!5e0!3m2!1shr!2shr!4v1755352133036!5m2!1shr!2shr" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
      </div>
    </div>

    <div class="contact_us_form_with_picture">
      <div class="contact_us_form_picture">
        <img src="../public/resources/images/contact_us_form_picture.jpg">
      </div>
      <div class="contact_us_form">
        <h1>Contact Us!</h1>
        <form @submit.prevent="sendEmail" class="contact-form">
          <input type="text" v-model="form.name" placeholder="Your Name" required />
          <input type="email" v-model="form.email" placeholder="Your Email" required />
          <input type="text" v-model="form.subject" placeholder="Subject" required />
          <textarea v-model="form.message" placeholder="Your Message" required></textarea>
          <button type="submit" :disabled="sending">
            {{ sending ? "SENDING..." : "SEND MESSAGE" }}
          </button>
          <p v-if="successMessage" class="success">{{ successMessage }}</p>
          <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
        </form>
      </div>
    </div>

  <Footer/>

</template>

<script setup>

import emailjs from "emailjs-com";

const form = reactive({
  name: "",
  email: "",
  subject: "",
  message: ""
});

const sending = ref(false);
const successMessage = ref("");
const errorMessage = ref("");

const sendEmail = () => {
  sending.value = true;
  successMessage.value = "";
  errorMessage.value = "";

  emailjs.send(
    "service_15f1lr4",
    "template_xzqhr5m",
    {
      from_name: form.name,
        from_email: form.email,
        subject: form.subject,
        message: form.message
    },
    "zuyTXYdtAGUw8lERn"
  )
  .then(() => {
    successMessage.value = "Message sent successfully!";
    form.name = "";
    form.email = "";
    form.subject = "";
    form.message = "";
  })
  .catch(() => {
    errorMessage.value = "Failed to send message. Please try again.";
  })
  .finally(() => {
    sending.value = false;
  });
};
</script>
  