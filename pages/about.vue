<template>
    <BackToTop/>
    <div class="about_intro_section">
      <Navigation/>
      <div class="about_intro_section_title">
        <h1>ABOUT US</h1>
      </div>
    </div>

    <div class="about_intro_section_text_and_image">
        <div class="about_intro_section_text">
            <h4>About us</h4>

            <h1>Pioneering Smart Coatings For a Sustainable And Cost-Effective Future.
            </h1>

            <p>Eninco Engineering d.o.o., established in Zagreb, Croatia in 2023, is a sister company to Eninco Engineering B.V. in the Netherlands. It operates the largest paint and resin research center in Central and Eastern Europe, and is focused on producing smart coatings using a technology derived from Eninco Engineering B.V. Bridging the gap between academia and industry, Eninco is dedicated to innovating and enhancing industrial coating systems.</p>

            <p>The company recruits and trains highly educated personnel, contributing to workforce retention. It is led by Dr. Arezoo Assarian, the inventor of the technology used to produce these smart coatings. These products, formulated to minimize costs, energy, labor, layers, and coating quantity, stem from over three decades of her research.</p>

            <p>Eninco’s innovative smart materials significantly improve chemical and mechanical properties while reducing environmental impact, especially in terms of VOC emissions. Despite the stagnancy of the paint and coating market, Eninco is pioneering change, offering comprehensive, cost-effective solutions to meet ever-evolving industrial needs.</p>

            <div class="button">
                <NuxtLink to="/products">OUR SERVICES</NuxtLink>
            </div>
        </div> 

        <div class="about_intro_section_image">
            <img src="../public/resources/images/brush.jpg">
        </div>
    </div>

    <div class="accomplishments_row">
        <div class="accomplishments" v-for="accomplishment  in accomplishments">
            <img :src="accomplishment .photo" />
            <div class="title_and_paragraf">
                <h2>{{ accomplishment .title }}</h2>
                <p>{{ accomplishment .paragraf }}</p>
            </div>
            
        </div>
    </div>

    <div class="our_team">
        <h4>The Team</h4>
        <h2>Our Experts</h2>
    </div>

    <div class="meet_our_team">
        <div class="meet_our_team_members" v-for="member in members">
            <div class="portrait">
                <img :src="member.photo" />
            </div>
            <h4>{{ member.title }}</h4>
            <h2>{{ member.name }}</h2>
            <p>{{ member.paragraf }}</p>
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
        :slidesPerView="2"
        :spaceBetween="100"
        :pagination="{ clickable: true }"
        :navigation="true"
        :autoplay="{
          delay: 3000,
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

    <div class="news" id="news">
      <h2>News</h2>
      <div class="news_articles" v-for="(article, index) in displayedArticles" :key="index">
            <div class="news_articles_photo" v-if="article.photo">
                <img :src="article.photo" />
            </div>
            <h3>{{ article.title }}</h3>
            <div class="calendar">
              <img :src="article.calendar"/>
              <h4>|</h4>
              <h4>{{article.date}}</h4> 
            </div>
            <p v-html="article.paragraf"></p>
        </div>
           <button class="quality_services_buttons" v-if="!showAll && articles.length > 3" @click="showAll = true">VIEW ALL</button>
        <NuxtLink to="#news" class="quality_services_buttons" v-if="showAll && articles.length > 3" @click="showAll = false">SHOW LESS</NuxtLink>
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

  const accomplishments = [
  {
    title: "500+",
    paragraf:
      "Successfully Project",
    photo: "../resources/images/project.png",
  },

  {
    title: "33",
    paragraf:
      "Year of experience",
    photo: "../resources/images/years_of_experience.png",
  },
 
];

  const members = [
  {
    title: "Innovator & CEO",
    name: "Dr. Arezoo Assarian",
    paragraf:
      "Dr. Arezoo Assarian holds a Ph.D. in Chemical Engineering. She is also a researcher, innovator, consultant, and an expert in manufacturing protective industrial coatings. With a deep knowledge of both the science of manufacturing industrial coatings and the real-world conditions for the application of these coatings, she has provided expert witness as well as consulting and inspection to a wide range of industries. Her knowledge about the coating manufacturing, allowed her to invent smart coatings that can be applied directly onto metal (carbon steel), wood, and all types of plastics surfaces. These coatings are all certified by SGS and TUV in EU.",
    photo: "../resources/images/Arezoo.jpg",
  },

  {
    title: "Executive Manager",
    name: "Ivan Dabro",
    paragraf:
      "Mr. Ivan Dabro has a B.Sc. Degree in Electromechanical Engineering and Automation, Faculty of Electrical Engineering, Zagreb, Croatia (ETF). He has more than 40 years of experience in various industries around the globe as a Project leader. He is currently holding the position of Executive Manager at Eninco Engineering B.V. as well as holding the position of Managing Director of Euro-S 2000 Ltd. (Since 1995).",
    photo: "../resources/images/Ivan.jpg",
  }
];

const articles = [
{
    title: "Interview with our founder",
    date: "27.8.2025",
    calendar: "../resources/images/calendar.png",
    paragraf:
     'Our Founder and CEO Arezoo Assarian was interviewed last week by Inspenet TV. We are so proud of our CEO and we hope you check out the interview! <br> <a href="https://inspenet.com/video-tv/recubrimientos-inteligentes-industriales" target="_blank">Watch Interview</a>',
    photo: "../resources/images/interview.jpg",
  },

];

const showAll = ref(false);

const displayedArticles = computed(() => {
  return showAll.value ? articles : articles.slice(0, 3);
});

</script>