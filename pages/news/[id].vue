<template>
    <div class="news_single_article_intro_section">
        <Navigation/>
    </div>
  <div v-if="article" class="news_page_single_article">
    <div class="news_page_single_article_photo" v-if="article.photo">
          <img :src="article.photo" />
          </div>
          <h3>{{ article.title }}</h3>
          <div class="news_page_single_article_calendar">
              <img :src="article.calendar" />
              <h4>|</h4>
              <h4>{{ article.date }}</h4>
          </div>
          <p v-html="article.paragraf"></p>
  </div>
  <div v-else>
    <p>Article not found.</p>
  </div>
</template>

<script setup>
import { useRoute } from "vue-router"
import { articles } from "~/data/articles"

const route = useRoute()
const article = articles[Number(route.params.id) - 1]
</script>
