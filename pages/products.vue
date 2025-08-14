<template>
    <BackToTop/>
    <div class="products_intro_section">
        <Navigation/>
        <div class="products_intro_section_text">
            <h1>PRODUCTS</h1>
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
  { url: "/resources/images/certifikat.png" },
  { url: "/resources/images/certifikat2.png" },
  { url: "/resources/images/certifikat3.png" },
  { url: "/resources/images/certifikat4.png" },
  { url: "/resources/images/certifikat5.png" },
  { url: "/resources/images/certifikat6.png" },
  { url: "/resources/images/certifikat7.png" },
  { url: "/resources/images/certifikat8.png" },
  { url: "/resources/images/certifikat9.png" },
  { url: "/resources/images/certifikat10.png" },
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
  