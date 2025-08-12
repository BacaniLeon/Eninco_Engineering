<template>
    <BackToTop/>
    <div class="intro_section">
        <Navigation/>
        <div class="intro_section_text">
            <h4>Quality In Every Brushstroke</h4>
            <h1>ENINCO ENGINEERING</h1>
            <p>Eninco Engineering d.o.o. is a Manufacturing, Consulting & Engineering Services firm that provides project consultancy in the field of paint and coating system engineering through technical excellence, innovation, and dedication. It offers comprehensive and cost-effective solutions for the successful execution of projects through its experts who possess a high level of professional competence.</p>
        </div>
        <div class="intro_section_buttons">
            <NuxtLink to="/products">OUR PRODUCTS</NuxtLink>
            <NuxtLink to="/contact">CONTACT US</NuxtLink>
        </div>
    </div>

    <div class="build_your_dream_with_img">
        <div class="build_your_dream_section">
            <h4>Build Your Dream</h4>
            <h1>33 Years Of Undefeated Success</h1>
            <p>Experience the magic of transformation with our eco-friendly paints and coatings, meticulously formulated to minimize environmental impact without compromising on quality. Join us in our commitment to a greener future, and let’s beautify your space while preserving our planet. Choose vibrant, sustainable living. Choose us.</p>
            <NuxtLink to="/services" class="work_with_us_button">WORK WITH US</NuxtLink>
        </div>
        <div class="build_your_dream_image">
            <img src="../public/resources/images/lighbulb.jpg">
        </div>
    </div>

    <div class="trust_and_worth">
    <h2>Trust and Worth</h2>
    <h1>Our Certificates</h1>
    <div class="swiperDiv">
      <Swiper
        effect="cube"
        :grabCursor="true"
        :centeredSlides="true"
        :slidesPerView="3"
        :spaceBetween="100"
        :pagination="{ clickable: true }"
        :navigation="true"
        :autoplay="{
          delay: 2000,
          disableOnInteraction: false,
          pauseOnMouseEnter: true
        }"
        :speed="5000"
        :modules="modules"
        class="mySwiper"
      >
        <SwiperSlide v-for="(photo, index) in photos" :key="index">
          <div class="slide-inner">
            <img class="img__ForHomePage" :src="photo.url" :alt="'cert-'+index" />
          </div>
        </SwiperSlide>
      </Swiper>
    </div>
  </div>

  <div class="quality_services">
  <div class="quality_services_adjusting">
      <h4>Build Your Dream</h4>
      <div class="quality_services_button_plus_title">
      <h1>Quality Services</h1>
        <button v-if="!showAll && services.length > 3" @click="showAll = true">VIEW ALL</button>
        <button v-else-if="showAll && services.length > 3" @click="showAll = false">SHOW LESS</button>
      </div>
      <div class="services_flex">
        <div class="services__Facts" v-for="(service, index) in displayedServices" :key="index">
          <img :src="service.photo" />
          <h2>{{ service.title }}</h2>
          <p>{{ service.paragraf }}</p>
        </div>
      </div>
    </div>
  </div>

  <div class="about_us_button">
    <NuxtLink to="/about">ABOUT US</NuxtLink>
  </div>

<div class="request_quote_and_faq_background">
  <div class="request_quote_and_faq">
    <div class="request_quote">
      <h1>Request a Quote</h1>
      <p>Ready to Work Together? Build a project with us!</p>
      <form @submit.prevent="sendEmail" class="contact-form">
        <input type="text" v-model="form.name" placeholder="Your Name" required />
        <input type="email" v-model="form.email" placeholder="Your Email" required />
        <input type="text" v-model="form.subject" placeholder="Subject" required />
        <textarea v-model="form.message" placeholder="Your Message" required></textarea>
        <button type="submit" :disabled="sending">
          {{ sending ? "Sending..." : "Send Message" }}
        </button>
        <p v-if="successMessage" class="success">{{ successMessage }}</p>
        <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
      </form>
    </div>

    <div class="faq">
      <h4>Learn More From</h4>
      <h1>Frequently Asked Questions</h1>
      <h2>Product Information</h2>
      <div class="faq_faq">
        <div
          v-for="(faq, index) in faqs"
          :key="index"
          class="faq-item"
          :class="{ open: faq.open }"
        >
          <div class="faq-question" @click="toggleFAQ(index)">
            <span>{{ faq.question }}</span>
            <span class="arrow">{{ faq.open ? "−" : "+" }}</span>
          </div>
          <div v-if="faq.open" class="faq-answer">
            {{ faq.answer }}
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
  <Footer/>

</template>

<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';
import 'swiper/css/effect-coverflow';
import 'swiper/css/pagination';
import { EffectCoverflow, Pagination, Autoplay } from 'swiper/modules';
import { reactive, ref } from "vue";
import emailjs from "emailjs-com";

const modules = [EffectCoverflow, Pagination, Autoplay];

const photos = [
    { url: "../resources/images/Certifikat.png" },
    { url: "../resources/images/Certifikat2.png" },
    { url: "../resources/images/Certifikat3.png" },
    { url: "../resources/images/Certifikat4.png" },
    { url: "../resources/images/Certifikat5.png" },
    { url: "../resources/images/Certifikat6.png" },
    { url: "../resources/images/Certifikat7.png" },
    { url: "../resources/images/Certifikat8.png" },
    { url: "../resources/images/Certifikat9.png" },
    { url: "../resources/images/Certifikat10.png" }
  ];

  const services = [
  {
    title: "Consulting Services",
    paragraf:
      "Coating Selection, Application Method Selection and Coating Consumption Management. ",
    photo: "../resources/images/consulting.jpg",
  },

  {
    title: "Educational Services",
    paragraf:
      "Variety of Training Courses.",
    photo: "../resources/images/education.jpg",
  },

  {
    title: "Inspection Services",
    paragraf:
      "Quality Control and more.",
    photo: "../resources/images/inspection.jpg",
  },

  {
    title: "Post-Sales Services",
    paragraf:
      "Product Warranty and After-sales Support",
    photo: "../resources/images/post_sale.jpg",
  },

  {
    title: "Post-Sales Services",
    paragraf:
      "Product Warranty and After-sales Support",
    photo: "../resources/images/post_sale.jpg",
  },

  {
    title: "Post-Sales Services",
    paragraf:
      "Product Warranty and After-sales Support",
    photo: "../resources/images/post_sale.jpg",
  },

  {
    title: "Post-Sales Services",
    paragraf:
      "Product Warranty and After-sales Support",
    photo: "../resources/images/post_sale.jpg",
  },

  {
    title: "Post-Sales Services",
    paragraf:
      "Product Warranty and After-sales Support",
    photo: "../resources/images/post_sale.jpg",
  },

  {
    title: "Post-Sales Services",
    paragraf:
      "Product Warranty and After-sales Support",
    photo: "../resources/images/post_sale.jpg",
  },

  {
    title: "Post-Sales Services",
    paragraf:
      "Product Warranty and After-sales Support",
    photo: "../resources/images/post_sale.jpg",
  },
];
const showAll = ref(false);

const displayedServices = computed(() => {
  return showAll.value ? services : services.slice(0, 3);
});


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


const faqs = ref([
  {
    question: "What types of coatings do you produce?",
    answer: "We produce a range of industrial and construction paints, including epoxy coatings, polyurethane coatings, acrylic coatings, and polyaspartic coatings.",
    open: false,
  },
  {
    question: "What surfaces can your coatings be applied to?",
    answer: "Our coatings can be applied to a wide variety of surfaces, including concrete, metal, wood, plastic, and masonry.",
    open: false,
  },
  {
    question: "What are the advantages of using your coatings over others on the market",
    answer: "Our coatings are specially formulated to provide excellent adhesion, durability, and resistance to chemicals, abrasion, and weathering. Additionally, our technical team can provide customized solutions to meet your specific needs.",
    open: false,
  },
]);

const toggleFAQ = (index) => {
  faqs.value[index].open = !faqs.value[index].open;
};

</script>
  