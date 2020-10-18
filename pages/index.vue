<template>
  <div class="main">
    <div class="main__container">
      <div class="main__menu">
        <ul>
          <li>
            Архитектура
          </li>
          <li>
            Благоустройство
          </li>
          <li>
            Безопастность
          </li>
          <li>
            Инженерия
          </li>
          <li>
            Инфраструктура
          </li>
          <li>
            Транспортная доступность
          </li>
        </ul>
      </div>
      <div class="main__content">
        <div class="main__text">
          <h1>Архитектура</h1>
          <p>
            Оригинальная архитектура жилого комплекса бизнес-класса
            «Первомайская» формирует современный стиль жизни
          </p>
          <div class="main__pages">
            <span>1 / 6</span>
          </div>
        </div>
      </div>
      <div class="main__illustration">
        <img src="@/assets/img/Illustration1.png" alt="">
      </div>
    </div>
  </div>
</template>

<script>
  export default {}
</script>

<style lang="scss">
  .main {
    width: 100%;
    &__container {
      display: flex;
      height: 100%;
    }

    &__menu {
      max-width: 280px;
      width: 100%;
      background: #fff;
      padding: 0 20px 0 0;
      display: flex;
      flex-direction: column;
      justify-content: center;

      ul {
        height: 251px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;

        li {
          padding: 0 4px;
          font-size: 13px;
          cursor: pointer;
          position: relative;
          color: #505050;
          z-index: 1;
          max-width: max-content;

          &::before{
            content: '';
            position: absolute;
            top: 9px;
            left: 0;
            z-index: -1;
            background: #EBD8CC;
            width: 100%;
            height: 9px;
            opacity: 0;
            transition: opacity .5s;
          }

          &:hover{
            &::before{
              opacity: 1;
            }
          }
        }
      }
    }

    &__content {
      display: flex;
      flex-direction: column;
      justify-content: center;
      max-width: 760px;
      width: 100%;
      align-items: center;
      padding: 0 20px;
    }

    &__text {
      max-width: 435px;
      width: 100%;

      h1 {
        font-size: 44px;
        margin-bottom: 40px;
      }

      p {
        font-size: 18px;
      }

      span {
        font-size: 17px;
      }
    }

    &__pages{
      margin-top: 150px;
    }

    &__illustration {
      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }
  }
</style>
