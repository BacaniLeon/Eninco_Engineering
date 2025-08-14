<template>
    <BackToTop/>
    <div class="products_intro_section">
      <Navigation/>
      <div class="products_intro_section_text">
        <h1>PRODUCTS</h1>
      </div>
    </div>

    <div class="our_products">
      <h4>Our Products</h4>
      <h1>Eninco Originals</h1>
    </div>

    <div class="list_of_products_flex">
  <div
    class="list_of_products"
    v-for="product in products"
    :key="product.id"
    :style="{ backgroundImage: `url(${product.photo})` }"
  >
    <h2>{{ product.title }}</h2>
    <p>{{ product.paragraf }}</p>
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

  const products = [
  {
    title: "SUPER LOTUS",
    paragraf:
      "Wood Lacquer",
    photo: "../resources/images/product.jpg",
  },

  {
    title: "ETERNAL",
    paragraf:
      "Metal Coating",
    photo: "../resources/images/product.jpg",
  },

  {
    title: "ENIWALL",
    paragraf:
      "Wall Paint",
    photo: "../resources/images/product.jpg",
  },

  {
    title: "ACRYLCOAT",
    paragraf:
      "Plastic Coating",
    photo: "../resources/images/product.jpg",
  }
];
const showAll = ref(false);

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
  