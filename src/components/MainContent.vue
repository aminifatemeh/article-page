<script setup>
import { inject, onMounted } from 'vue'
import TextContent from '@/components/TextContent.vue'
import Sidebar from '@/components/MainSection/Sidebar.vue'

const article = inject('article')
const tags = inject('tags')
const headings = inject('headings')
//add IDs to the headings in the article content
const addToElements = () => {
  const headings = document.getElementsByTagName('h2')
  for (let index = 0; index < headings.length; index++) {
    headings[index].id = `headings-${index}`
  }
}

onMounted(() => {
  addToElements()
})
</script>

<template>
  <section class="main-content">
    <text-content :article="article" :tags="tags"></text-content>
    <sidebar :headings="headings"></sidebar>
  </section>
</template>

<!--removing scoped in order to be able to style dynamically added elements-->
<style lang="scss">
@import '../assets/sass/_colors.scss';

.main-content {
  width: 100%;
  height: 100%;
  display: flex;
}
</style>
