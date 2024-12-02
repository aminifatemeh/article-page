<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import axios from 'axios'

const relatedArticles = ref([])
const slides = ref([])
const cardsCount = ref(3)
const fetchRelatedArticles = async () => {
  try {
    const response = await axios.get('https://api.sokanacademy.com/api/related', {
      params: {
        entity_type: 'blog',
        entity_slug: '8-common-data-structures-every-programmer-must-know',
        domain: 'blog,section,course,word',
        take: 6
      }
    })
    relatedArticles.value = response.data.data
    createSlides()
  } catch (error) {
    console.log('error fetching data', error)
  }
}

const createSlides = () => {
  slides.value = []
  for (let i = 0; i < relatedArticles.value.length; i += cardsCount.value) {
    slides.value.push(relatedArticles.value.slice(i, i + cardsCount.value))
  }
}

const updateCardCount = () => {
  const width = window.innerWidth
  if (width < 768) {
    cardsCount.value = 1
  } else if (width < 992) {
    cardsCount.value = 2
  } else {
    cardsCount.value = 3
  }
  createSlides()
}

const resizeObserver = new ResizeObserver(updateCardCount)

onMounted(() => {
  fetchRelatedArticles()
  updateCardCount()
  resizeObserver.observe(document.body)
})

onBeforeUnmount(() => {
  resizeObserver.disconnect()
})
</script>

<template>
  <section class="related-articles">
    <div class="d-flex gap-3 align-items-center">
      <span class="heading-line"></span>
      <span class="heading-3 right">مطالب مرتبط</span>
      <span class="heading-line"></span>
    </div>
    <div id="carouselExampleIndicators" class="carousel slide">
      <div class="carousel-indicators d-flex gap-3">
        <div>
          <button
            class="carousel-control-next"
            type="button"
            data-bs-target="#carouselExampleIndicators"
            data-bs-slide="next"
          >
            <img src="../assets/icons/arrow-right-2.svg" alt="" />
          </button>
        </div>
        <div v-if="slides.length">
          <button
            v-for="(slide, index) in slides"
            :key="index"
            type="button"
            data-bs-target="#carouselExampleIndicators"
            :data-bs-slide-to="index"
            class="slider-button"
            :class="{ active: index === 0 }"
            :aria-current="index === 0 ? 'true' : 'false'"
            :aria-label="'slide' + (index + 1)"
          ></button>
        </div>
        <div>
          <button
            class="carousel-control-prev"
            type="button"
            data-bs-target="#carouselExampleIndicators"
            data-bs-slide="prev"
          >
            <img src="../assets/icons/arrow-left-2.svg" alt="" />
          </button>
        </div>
      </div>
      <div class="carousel-inner">
        <div
          class="carousel-item"
          v-for="(slide, slideIndex) in slides"
          :key="slideIndex"
          :class="{ active: slideIndex === 0 }"
        >
          <div class="articles-group">
            <div class="article-card" v-for="item in slide" :key="item.entity_id">
              <img
                :src="item.cover_path || 'src/assets/images/fallback-img-small.webp'"
                alt="cover image"
              />
              <div class="article-card_content">
                <div class="d-flex flex-column gap-4 w-100">
                  <span class="title-2 artice-content_title" style="height: 72px">{{
                    item.title
                  }}</span>
                  <div class="d-flex gap-2">
                    <img
                      style="width: 21px; height: 21px"
                      :src="item.author.avatar || 'src/assets/images/image.png'"
                      alt="author avatar"
                    />
                    <span class="meta-1 right">{{ item.author.full_name }}</span>
                  </div>
                </div>
                <div class="d-flex justify-content-between w-100">
                  <div class="d-flex gap-3">
                    <div class="d-flex gap-2 align-items-center">
                      <img
                        style="width: 20px; height: 20px"
                        src="../assets/icons/category.svg"
                        alt=""
                      />
                      <span class="meta-1 right">{{ item.category_name }}</span>
                    </div>
                    <div class="d-flex gap-2 align-items-center">
                      <img
                        style="width: 20px; height: 20px"
                        src="../assets/icons/star-circle.svg"
                        alt=""
                      />
                      <span class="meta-1 right">{{ item.visits_count }}</span>
                    </div>
                  </div>
                  <img
                    style="width: 24px; height: 24px"
                    src="../assets/icons/Bookmark.svg"
                    alt=""
                  />
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
@import '../assets/sass/_colors.scss';

.related-articles {
  width: 100%;
  height: 100%;
  margin: 80px 0;
  padding: 0;
  background: linear-gradient(
    180deg,
    rgba(228, 225, 243, 0.1) 0%,
    rgba(228, 225, 243, 0.8) 50%,
    rgba(228, 225, 243, 0.1) 100%
  );
  display: flex;
  gap: 48px;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  .heading-line {
    width: 24px;
    height: 6px;
    background-color: $secondary-1-20;
    border-radius: 4px;
  }

  #carouselExampleIndicators {
    padding: 40px 20px 80px 20px;
    margin-bottom: 30px;
    .carousel-inner {
      border-radius: 20px;
    }
    .carousel-indicators {
      gap: 16px;
      .slider-button {
        width: 10px;
        height: 10px;
        background-color: black;
        border-radius: 100%;
      }
      div {
        height: 20px;
        position: relative;
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 0 20px;
      }
    }
    .articles-group {
      width: 100%;
      display: flex;
      flex: auto;
      justify-content: center;
      align-items: center;
      padding: 0;
      gap: 16px;
      .article-card {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 0;
        height: 236px;
        position: relative;
        border-radius: 20px;
        border: 2px solid $grayscale-2;
        overflow: hidden;
        &:hover {
          .article-card_content {
            top: 0;
          }
        }
        img:first-child {
          width: 100%;
          height: 100%;
          border-radius: 6px;
        }
        .article-card_content {
          position: absolute;
          width: 100%;
          height: 100%;
          display: flex;
          flex-direction: column;
          justify-content: space-between;
          align-items: flex-end;
          padding: 20px;
          border-radius: 20px;
          background: rgba(255, 255, 255, 0.88);
          top: 55%;
          transition: 350ms ease;
          .artice-content_title {
            display: -webkit-box;
            -webkit-box-orient: vertical;
            -webkit-line-clamp: 2;
            overflow: hidden;
            text-overflow: ellipsis;
            max-height: calc(36px * 2);
          }
        }
      }
    }
  }
}
</style>
