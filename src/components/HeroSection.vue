<script setup>
import { inject, defineProps, computed } from 'vue'
const props = defineProps({
  article: {
    type: Object,
    required: true
  }
})

const author = inject('author')
const category = inject('category')

const calDate = computed(() => {
  const date = new Date(props.article.created_at)
  const seconds = Math.floor(date.getTime() / 1000)
  const currentTime = Math.floor(Date.now() / 1000)
  const difference = currentTime - seconds
  return `${Math.floor(difference / 31536000)} سال پیش`
})
</script>

<template>
  <section class="hero-section">
    <div class="hero-content">
      <div class="hero_title-content">
        <span class="heading-2 right">{{ article.title }}</span>
        <div class="hero_metadata-avatar">
          <div class="hero_metadata">
            <div>
              <img src="../assets/icons/category.svg" alt="category" />
              <span class="body right">{{ category.name }}</span>
            </div>
            <div>
              <img src="../assets/icons/calendar.svg" alt="calendar" /><span class="body right">{{
                calDate
              }}</span>
            </div>
            <div>
              <img src="../assets/icons/clock.svg" alt="clock" />
              <span class="body right">{{ article.article?.duration }} دقیقه</span>
            </div>
            <div>
              <img src="../assets/icons/star-circle.svg" alt="star circle" /><span
                class="body right"
                >651 امتیاز</span
              >
            </div>
          </div>
          <div class="hero_avatar">
            <img :src="author.avatar || 'src/assets/images/image.png'" alt="avatar image" />
            <span class="title-3">{{ author.full_name }}</span>
            <img src="../assets/icons/verify.svg" alt="" />
          </div>
        </div>
      </div>
      <div class="hero_cover-image">
        <img
          :src="article.cover || 'src/assets/images/fallback-img-small.webp'"
          alt="cover image"
        />
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import '../assets/sass/_colors.scss';

.hero-section {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 140px 20px 140px 20px;

  .hero-content {
    width: 100%;
    gap: 112px;
    display: flex;
    justify-content: center;

    .hero_title-content {
      display: flex;
      flex-direction: column;
      width: 656px;
      gap: 36px;
      span {
        color: $secondary-2-100;
      }
      .hero_metadata-avatar {
        display: flex;
        flex-direction: column;
        gap: 36px;
        .hero_metadata {
          display: flex;
          gap: 24px;
          div {
            display: flex;
            gap: 8px;
          }
        }
        .hero_avatar {
          display: flex;
          gap: 4px;
          align-items: center;
          img:nth-child(1) {
            margin-left: 4px;
            width: 24px;
            height: 24px;
            border-radius: 6px;
            border: 1px;
          }
        }
      }
    }

    .hero_cover-image {
      display: flex;
      justify-content: center;
      align-items: center;
      img {
        width: 368px;
        height: 236px;
        border-radius: 20px;
        border: 1px;
      }
    }
  }
}

//MEDIA QUERIES

// Medium devices (tablets, 768px and down)
@media (max-width: 992px) {
  .hero-section {
    flex-direction: column;
    .hero-content {
      flex-direction: column;
      gap: 21px;
      .hero_title-content {
        width: 100%;
        order: 1;
        .hero_metadata {
          flex-wrap: wrap;
          div {
            width: calc(50% - 24px);
          }
        }
      }
      .hero_cover-image {
        order: 0;
      }
    }
  }
}
</style>
