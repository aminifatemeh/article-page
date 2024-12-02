<script setup>
import { inject } from 'vue'

const author = inject('author')
</script>

<template>
  <section class="author-section">
    <div class="author_description-card">
      <div class="author_image">
        <img :src="author.avatar || 'src/assets/images/image.png'" alt="" />
      </div>
      <div class="author_content">
        <div class="author_name">
          <span class="title-3">{{ author.full_name }}</span>
          <span class="subtitle-1 right">{{ author.bio }} </span>
        </div>
        <div class="author_button">
          <button class="meta-1 right">مشاهده پروفایل</button>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@import '../assets/sass/_colors.scss';
.author-section {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 20px 80px 20px;
  .author_description-card {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;
    border-radius: 20px;
    border: 2px solid #e6e6e6;
    padding: 24px;
    .author_image {
      img {
        width: 145px;
        height: 145px;
        border-radius: 12px;
      }
    }
    .author_content {
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      .author_name {
        display: flex;
        flex-direction: column;
        gap: 8px;
        span:first-child {
          color: #0b032d;
        }
        span:nth-child(2) {
          display: -webkit-box;
          -webkit-box-orient: vertical;
          -webkit-line-clamp: 2;
          overflow: hidden;
          text-overflow: ellipsis;
          max-height: calc(36px * 2);
          color: #4a4a4a;
        }
      }
      .author_button {
        width: 100%;
        display: flex;
        justify-content: end;
        button {
          height: 37px;
          display: flex;
          justify-content: center;
          align-items: center;
          padding: 0 10px;
          gap: 6px;
          border: 1px solid #0b032d;
          border-radius: 8px;
          text-wrap: nowrap;
          background-color: transparent;
          color: #0b032d;
        }
      }
    }
  }
}

@media (max-width: 576px) {
  .author-section {
    width: 100%;
    height: 100%;
  }
  .author_description-card {
    flex-direction: column;
    height: 100%;
    width: 100%;
  }
}
</style>
