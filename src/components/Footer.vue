<script setup>

</script>

<template>
  <footer>
    <div class="footer-body">
      <div class="footer-container">
        <!--FOOTER PARAGRAPH-->
        <div class="paragraph-container col-lg-5 justify-content-lg-end" style="">
          <img src="../assets/images/Logo.svg" alt="">
          <p class="subtitle-1 right">ما در سکان‌آکادمی معتقدیم همه‌ی انسان‌ها حق دارند، به آموزش باکیفیت و کم‌هزینه دسترسی آسان داشته باشند و همه‌ی افراد می‌توانند با آموزش درست، زندگی فردی و اجتماعی خود را بهتر کنند. با توجه به تخصص تیم ما در حوزه‌ی IT و نیاز روزافزون بازار کار به متخصصان این حوزه، تولید و عرضه‌ی محتوای مهارت‌محور و تخصصی را در حوزه‌ی IT جدی‌تر دنبال کردیم. در این راه از ابتدای انتخاب مسیر متناسب با توانایی و امکانات دانشجو تا یادگیری، تمرین، کسب مهارت تخصصی و عمومی، و در نهایت معرفی به بازار کار همراه او هستیم...</p>
        </div>
        <!--FOOTER MENU-->
        <div class="footer-menu-container">
          <div>
            <ul>
              <li class="list-group title-3">خدمات سکان آکادمی</li>
              <li class="list-group subtitle-1 right">دوره های آموزشی</li>
              <li class="list-group subtitle-1 right">وبلاگ</li>
              <li class="list-group subtitle-1 right">سکان پلاس</li>
              <li class="list-group subtitle-1 right">رادیو فول استک</li>
              <li class="list-group subtitle-1 right">فن واژه</li>
            </ul>
          </div>
          <div>
            <ul>
              <li class="list-group title-3">دسترسی سریع</li>
              <li class="list-group subtitle-1 right">درباره ما</li>
              <li class="list-group subtitle-1 right">تماس با ما</li>
              <li class="list-group subtitle-1 right">همکاری با ما</li>
              <li class="list-group subtitle-1 right">شرایط و قوانین</li>
            </ul>
          </div>
        </div>

      </div>
      <div>
        <p class="copyright title-4 center">کلیه حقوق مادی و معنوی این وب‌سایت متعلق به سکان آکادمی می‌باشد.</p>
      </div>
    </div>

  </footer>

</template>

<style lang="scss" scoped>
@import "../assets/sass/_colors.scss";

.footer-body{
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 48px 20px 48px 20px;
  background-color: $grayscale-1;
  gap: 40px;
  .footer-container{
    width: 100%;
    display: flex;
    justify-content: space-evenly;
    color: $secondary-2-100;
    .paragraph-container{
      img{
        margin-bottom: 20px;
      }
    }
    .footer-menu-container{
      display: flex;
      div{
        height: 100%;
        ul{
          display: flex;
          flex-direction: column;
          gap: 12px;
        }
      }
    }
  }
}

//MEDIA QUERIES

// Small devices (landscape phones, 576px and down)
@media (max-width: 576px) {

  .paragraph-container{
    min-width: 328px;
  }
  .footer-container{
    flex-direction: column;
  }
}

// Small devices (landscape phones, 576px and up)
@media (min-width: 576px){
  .footer-container{
    flex-direction: column;
  }
  .footer-menu-container{
    justify-content: space-evenly;
  }
}


// Medium devices (tablets, 768px and up)
@media (min-width: 768px) {
  .paragraph-container{
    width: 328px;
  }
  .footer-container{
    flex-direction: row;
  }
}

// Large devices (desktops, 992px and up)
@media (min-width: 992px) {
  .paragraph-container{
    width: 500px;
  }

}

// X-Large devices (large desktops, 1200px and up)
@media (min-width: 1200px) {
  .paragraph-container{
    width: 656px;
  }
}

// XX-Large devices (larger desktops, 1400px and up)
@media (min-width: 1400px) {
  .footer-menu-container{
    gap: 20px;
  }

}
</style>