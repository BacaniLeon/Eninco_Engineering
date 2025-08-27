<template>
    <BackToTop/>
    <div class="news_intro_section">
    <Navigation/>
      <div class="news_page_title">
        <h1>NEWS</h1>
      </div>
    </div>
  
    <div class="news_page_news">
        <div
        v-for="(article, index) in displayedArticles"
        :key="index"
        class="news_page_articles"
        >
        <div class="news_page_articles_photo" v-if="article.photo">
        <NuxtLink :to="`/news/${index+1}`"><img :src="article.photo" /></NuxtLink>
        </div>
        <NuxtLink :to="`/news/${index+1}`"><h3>{{ article.title }}</h3></NuxtLink>
        <div class="news_page_calendar">
            <img :src="article.calendar" />
            <h4>|</h4>
            <h4>{{ article.date }}</h4>
        </div>
        <p v-html="article.preview_paragraf"></p>
        <NuxtLink :to="`/news/${index+1}`"><h5>Click Here to read Full article</h5></NuxtLink>
        </div>
    </div>
    <div class="news_button_container">
          <button class="news_button" v-if="visibleCount < articles.length" @click="loadMore">SHOW MORE</button>
    </div>
  <Footer/>

</template>

<script setup>
import { ref, computed } from "vue"
import { articles } from "~/data/articles"

const visibleCount = ref(3)

const displayedArticles = computed(() => {
  return articles.slice(0, visibleCount.value)
})

const loadMore = () => {
  visibleCount.value += 3
}


</script>
  