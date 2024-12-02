<template>
  <section class="comment-section">
    <div class="comment_content">
      <div class="content_heading">
        <span class="heading-line"></span>
        <span class="heading-3 right">دیدگاه شما</span>
        <span class="heading-line"></span>
      </div>
      <div class="content_comment-box">
        <div class="d-flex gap-3 align-items-center">
          <img src="../assets/icons/Bullet Rectangle.svg" alt="" />
          <span class="title-3">دیدگاه یا پرسش جدید</span>
        </div>
        <div class="comment-box_textarea">
          <textarea class="meta-1 right">
دیدگاه یا پرسش خود را درباره این محتوا بنویسید...</textarea
          >
        </div>
        <div class="d-flex justify-content-end">
          <button>
            <span class="title-4 center">ارسال دیدگاه</span>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import '../assets/sass/_colors.scss';
.comment-section {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 80px 20px;
  .comment_content {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 48px;
    .content_heading {
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 12px;
      .heading-line {
        width: 24px;
        height: 6px;
        background-color: $secondary-1-20;
        border-radius: 4px;
      }
    }
    .content_comment-box {
      height: 269px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      padding: 20px;
      border-radius: 20px;
      border: 2px solid $grayscale-2;
      .comment-box_textarea {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 8px 16px 12px;
        gap: 12px;
        width: 100%;
        height: 128px;
        border-radius: 12px;
        background-color: $grayscale-1;
        textarea {
          width: 100%;
          height: 100%;
          border: none;
          resize: none;
          background-color: $grayscale-1;
          color: $grayscale-6;
        }
      }
      button {
        border: none;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 8px 12px;
        width: 97px;
        height: 37px;
        background-color: $grayscale-4;
        border-radius: 8px;
        color: $grayscale-3;
      }
    }
  }
}

//MEDIA QUERIES

// Large devices (desktops, 992px and up)
@media (min-width: 992px) {
  .content_comment-box {
    width: 800px;
  }
}

// Large devices (desktops, 992px and up)
@media (max-width: 992px) {
  .content_comment-box {
    width: 100%;
  }
}
</style>
