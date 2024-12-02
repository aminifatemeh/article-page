<script setup>
import { defineProps } from 'vue'

//defining props that this component receives
const props = defineProps(['article', 'tags'])
</script>

<template>
  <div class="main-content_text col-lg-8 col-md-12">
    <div class="text_content" v-html="article.article?.text"></div>
    <div class="text_tags-report">
      <div class="tag-group">
        <button v-for="tag in tags" :key="tag.id">{{ tag.name }}</button>
      </div>
      <div class="d-flex justify-content-end w-100">
        <button class="report-button title-4 center">
          <img src="../assets/icons/flag.svg" alt="flag icon" />گزارش محتوا
        </button>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
@import '../assets/sass/_colors.scss';
@import '../assets/sass/_mixin.scss';

.main-content_text {
  height: 100%;
  padding: 80px 20px 40px 48px;
  display: flex;
  flex-direction: column;
  justify-content: end;
  align-items: end;
  p,
  li {
    @include font-style(IRANSansXFaNum, 16px, 500, 32px, right);
  }
  h3 {
    @include font-style(IRANYekanXFaNum, 24px, 900, 48px, right);
  }
  h2 {
    @include font-style(IRANYekanXFaNum, 28px, 900, 56px, right);
  }
  button {
    @include font-style(IRANSansXFaNum, 14px, 500, 21px, center);
  }
  .text_content {
    display: flex;
    flex-direction: column;
    gap: 32px;
    color: $secondary-2-100;
    a {
      text-decoration: none;
      color: $secondary-1-100;
    }

    .image {
      img {
        width: 100%;
        border: 1px solid $grayscale-3;
      }
    }

    figcaption {
      display: flex;
      justify-content: center;
      align-items: center;
      margin-top: 15px;
      color: $grayscale-5;
      @include font-style(IRANSansXFaNum, 14px, 700, 33.6px, right);
    }
  }
  .text_tags-report {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 20px;
    .tag-group {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      button {
        height: 37px;
        text-wrap: nowrap;
        background-color: $grayscale-2;
        border: none;
        padding: 8px 10px;
        border-radius: 8px;
      }
    }
    .report-button {
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
    }
  }
}

@media (max-width: 992px) {
  .main-content {
    justify-content: center;
    align-items: center;
    .main-content_text {
      padding: 20px;
    }
  }
}
</style>

<!--
spacing in paragraphs
headers: margin-bottom:20px
paragraphs &  ul: 32px
image class: 32px

-->
