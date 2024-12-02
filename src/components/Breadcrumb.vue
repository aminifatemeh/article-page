<script setup>

</script>

<template>
  <nav class="breadcrumb-container" aria-label="breadcrumb">
    <ol class="breadcrumb">
      <li class="breadcrumb-item subtitle-1 right" aria-current="page">خانه</li>
      <img class="mx-2" src="../assets/icons/arrow-left.svg" alt="">
      <li class="breadcrumb-item subtitle-1 right"><a href="#">وبلاگ</a></li>
      <img class="mx-2" src="../assets/icons/arrow-left.svg" alt="">
      <li class="breadcrumb-item subtitle-1 right"><a href="#">برنامه نویسی</a></li>
      <img class="mx-2" src="../assets/icons/arrow-left.svg" alt="">
      <li class="breadcrumb-item title-4 right"><a href="#">هک کردن گوشی های اندرویدی با وارد کردن یک کلمه عبور بسیار طولانی</a></li>
    </ol>
  </nav>

</template>

<style lang="scss" scoped>
@import "../assets/sass/_colors.scss";

.breadcrumb-container{
  display: flex;
  align-items: center;
  padding: 0 ;

  .breadcrumb{
    height: 28px;

    .breadcrumb-item{
      a{
        text-decoration:none;
        color: $secondary-2-100;
      }

    }
    li:nth-child(7){
      a{
        color: $grayscale-5;
      }

    }
  }

}

//MEDIA QUERIES
// Small devices (landscape phones, 576px and down)
@media (max-width: 576px) {
  .breadcrumb-container{
    margin: 20px 16px 0 16px;
  }
}

// Small devices (landscape phones, 576px and up)
@media (min-width: 576px){
  .breadcrumb-container{
    margin: 20px 40px;
  }
}


// Medium devices (tablets, 768px and up)
@media (min-width: 768px) {
  .breadcrumb-container{
    margin: 20px 40px;
  }

}


// Large devices (desktops, 992px and up)
@media (min-width: 992px) {
  .breadcrumb-container{
    margin: 40px 80px;
  }

}

</style>