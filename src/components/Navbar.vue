<script setup>

</script>

<template>
  <nav class="navbar navbar-expand-lg">
    <div class="container d-flex align-items-center justify-content-between m-0">

      <!--logo-->
      <div class="logo-container d-lg-inline-block">
        <a class="navbar-brand" href="#">
          <img src="../assets/images/Logo.svg" alt="">
        </a>
      </div>

      <!--TOGGLER BUTTON-->
      <button class="navbar-toggler d-lg-none" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasNavbar" aria-controls="offcanvasNavbar" aria-label="Toggle navigation">
        <img src="../assets/icons/menu.svg" alt="menu icon">
      </button>

      <!--OFFCANVAS-->
      <div class="offcanvas offcanvas-end" tabindex="-1" id="offcanvasNavbar" aria-labelledby="offcanvasNavbarLabel">
        <div class="offcanvas-header d-lg-none">
          <button type="button" class="btn-close d-lg-none mx-0" data-bs-dismiss="offcanvas" aria-label="Close"></button>
        </div>
        <div class="offcanvas-body ">

          <!--NAV MENU-->
          <ul class="navbar-nav subtitle-1 center justify-content-lg-center align-items-lg-center me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <img src="../assets/icons/academy.svg" alt="">
              <a class="nav-link" href="#">دوره های آموزشی</a>
            </li>
            <li class="li-underline nav-item title-4 center">
              <img src="../assets/icons/weblog.svg" alt="">
              <a class="nav-link active" aria-current="page" href="#">وبلاگ</a>
              <span class="item-underline d-lg-inline-block"></span>
            </li>
            <li class="nav-item">
              <img src="../assets/icons/collection.svg" alt="">
              <a class="nav-link " href="#">مجموعه ها</a>
            </li>
            <li class="nav-item">
              <img src="../assets/icons/podcast.svg" alt="">
              <a class="nav-link " href="#">رادیو فول استک</a>
            </li>
            <li class="nav-item">
              <img src="../assets/icons/glossary.svg" alt="">
              <a class="nav-link "  href="#">فن واژه</a>
            </li>
          </ul>
        </div>
      </div>

      <!--LOGIN BUTTON-->
      <div class="btn-container">
        <button class="btn" type="button"><img src="../assets/icons/login.svg" alt=""><span class="d-none d-lg-inline-block mx-2 title-4 center">ورود | ثبت نام</span></button>
      </div>

    </div>

  </nav>

</template>

<style lang="scss" scoped>
@import "../assets/sass/_colors.scss";

.navbar{

  align-items: center;
  justify-content: center;
  margin-top: 24px;
  .logo-container{
    order: 1;
    a{
      margin: 0;
    }
    img{
      width: 87px;
      height: 37px;
    }
  }

  .navbar-toggler{
    order: 0;
    width: 37px;
    height: 37px;
    padding: 0;
    border: 1px solid $secondary-2-100;
  }

  .offcanvas{
    order: 2;
    .offcanvas-header{
      display: flex;
      justify-content: end;
      align-items: end;
    }
    .offcanvas-body{

      ul{
        display: flex;
        align-items: start;
        width: 100%;

        li{
          margin-left: 0.5rem;
          margin-right: 0.5rem;
          a{
            color: $secondary-2-100;
            text-wrap: nowrap;
          }
        }
        .li-underline{
          display: flex;
          align-items: center;
          justify-content: center;
          position: relative;
          a{
            color: $secondary-1-100;
          }
          .item-underline{
            width: 16px;
            height: 2px;
            background-color: $secondary-1-100;
            display: none;
            position: absolute;
            top: 55px;
            border-radius: 1px;
          }
        }
      }
    }
  }
  .btn-container{
    order:3;

    button{
      background-color: $secondary-2-100;
      color: $grayscale-0;
      padding: 8px 10px 8px 12px;
      border-radius: 8px;
      &:hover{
        background-color: $secondary-2-100;
      }
    }
  }
}


// Large devices (desktops, 992px and up)
@media (min-width: 992px) {
  .nav-item{
    img{
      display: none;
    }
  }
  .li-underline{
    flex-direction: column;
  }

}
@media (max-width: 992px) {
  .navbar-nav{
    gap: 15px;
  }
  .nav-item{
    display: flex;
    gap: 10px;
    .li-underline{
      flex-direction: row;
    }
  }
  .btn-container{
    img{
      width: 20px;
      height: 20px;
    }
  }
}

</style>