<script setup>
import { ref, onMounted, provide } from 'vue'
import Navbar from '@/components/Navbar.vue'
import Breadcrumb from '@/components/Breadcrumb.vue'
import HeroSection from '@/components/HeroSection.vue'
import MainContent from '@/components/MainContent.vue'
import RecommendedArticle from '@/components/RecommendedArticle.vue'
import AuthorSection from '@/components/AuthorSection.vue'
import CommentSection from '@/components/CommentSection.vue'
import Footer from '@/components/Footer.vue'

import axios from 'axios'

//reactive properties for the article, tags and headings
const article = ref({})
const tags = ref([])
const author = ref({})
const category = ref({})
const headings = ref([])

//fetch article data from the API
const fetchArticle = async () => {
  try {
    const response = await axios.get(
      'https://api.sokanacademy.com/api/blogs/8-common-data-structures-every-programmer-must-know'
    )
    article.value = response.data.data
    tags.value = article.value.tags
    author.value = article.value.author
    category.value = article.value.category
    extractHeadings(article.value.article.text)
  } catch (e) {
    console.error('error fetching data', e)
    return null
  }
}

//functions to extract headings from article text
const extractHeadings = (articleText) => {
  const parser = new DOMParser()
  const doc = parser.parseFromString(articleText, 'text/html')
  headings.value = []
  const h2Tags = doc.getElementsByTagName('h2')
  headings.value = Array.from(h2Tags).map((h2) => {
    return h2.innerText.trim()
  })
}

//provide dependencies to child components
provide('fetchArticle', fetchArticle)
provide('article', article)
provide('tags', tags)
provide('author', author)
provide('headings', headings)
provide('category', category)

onMounted(async () => {
  await fetchArticle()
})
</script>

<template>
  <div id="id">
    <Navbar />
    <Breadcrumb />
    <HeroSection :article="article" />
    <MainContent />
    <RecommendedArticle />
    <AuthorSection />
    <commentSection />
    <Footer />
  </div>
</template>

<style scoped></style>
