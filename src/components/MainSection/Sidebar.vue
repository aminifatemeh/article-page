<script setup>
import { defineProps } from 'vue'
const props = defineProps({
  headings: {
    type: Array,
    required: true
  }
})

const scrollToHeading = (index) => {
  const heading = document.getElementById(`headings-${index}`)
  if (heading) {
    heading.scrollIntoView({ behavior: 'smooth', block: 'start' })
  } else {
    console.warn('not found')
  }
}
</script>

<template>
  <div class="main-content_sidebar col-4">
    <div class="sidebar_content">
      <div class="table-of-content">
        <div class="d-flex gap-2">
          <img src="../../assets/icons/list.svg" alt="" />
          <span class="heading-6 right">در این مقاله میخوانید</span>
        </div>

        <ul>
          <li
            v-for="(heading, index) in headings"
            :key="index"
            @click.prevent="scrollToHeading(index)"
          >
            <img src="../../assets/icons/line.svg" alt="" />
            <a class="subtitle-1 right" href="#">{{ heading }}</a>
          </li>
        </ul>
      </div>
      <div class="action-buttons">
        <div class="d-flex justify-content-center align-items-center gap-2">
          <img src="../../assets/icons/comment.svg" alt="" />
          <span class="title-3 center">دیدگاه شما</span>
        </div>

        <div class="d-flex justify-content-center align-items-center gap-3">
          <img src="../../assets/icons/Bookmark.svg" alt="" />
          <img src="../../assets/icons/Link%20Icon.svg" alt="" />
          <img src="../../assets/icons/Share%20Icon.svg" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@import '../../assets/sass/colors';

.main-content_sidebar {
  position: relative;
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  padding: 0 0 40px 20px;
  gap: 10px;
  .sidebar_content {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 16px;
    height: 392px;
    top: 20px;
    position: sticky;
    z-index: 1000;
    .table-of-content {
      width: 368px;
      height: 300px;
      border: 2px solid $grayscale-2;
      background-color: $grayscale-0;
      padding: 20px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      border-radius: 16px;
      overflow: auto;

      &::-webkit-scrollbar {
        width: 4px;
      }
      &::-webkit-scrollbar-track {
        border-radius: 12px;
        margin: 5px 0;
      }
      &::-webkit-scrollbar-thumb {
        background: $grayscale-4;
        width: 4px;
        border-radius: 12px;
      }

      li {
        display: flex;
        width: 100%;
        border-radius: 10px;
        padding: 12px;
        gap: 12px;
        &:hover {
          background-color: $grayscale-1;
        }
        a {
          color: $secondary-2-100;
          text-decoration: none;
        }
      }
    }
    .action-buttons {
      width: 100%;
      height: 76px;
      display: flex;
      justify-content: space-between;
      border-radius: 16px;
      border: 2px solid $grayscale-2;
      background-color: $grayscale-0;
      padding: 16px 20px;
    }
  }
}

@media (max-width: 992px) {
  .main-content_sidebar {
    display: none;
    .text_content {
      justify-content: center;
      align-items: center;
    }
  }
}
</style>
