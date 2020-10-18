<template>
  <div class="header">
    <div class="header__container">
      <div class="header__logo">
        <h1>Первомайская</h1>
      </div>
      <div class="header__menu">
        <ul>
          <li>
            <nuxt-link to="/">О комплексе</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/features">Особенности</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/features">Пентхаусы</nuxt-link>
          </li>
          <li>
            <nuxt-link to="/features">Выбрать квартиру</nuxt-link>
          </li>
        </ul>
      </div>
      <div class="header__contact">
        <h1>8 888 888 88 88</h1>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'TopBar',
  }
</script>

<style scoped lang="scss">
  .header {
    max-width: 1920px;
    width: 100%;
    height: 60px;
    background: #fff;
    position: relative;
    text-transform: uppercase;

    &::before {
      content: '';
      position: absolute;
      background: url('/img/header/IconLogo.png') no-repeat;
      max-width: 70px;
      width: 100%;
      height: 70px;
      top: 25px;
      left: -35px;
      z-index: 1;
    }

    &::after {
      content: '';
      position: absolute;
      background: url('/img/header/Burger.png') no-repeat;
      max-width: 70px;
      width: 100%;
      height: 70px;
      top: 25px;
      right: -35px;
      z-index: 1;
    }

    &__container {
      /*max-width: 1800px;*/
      width: 100%;
      padding: 0 60px;
      /*padding: 0 125px;*/
      margin: 0 auto;
      display: flex;
      align-items: center;
      height: 100%;
      justify-content: space-between;
    }

    &__logo {
      padding-right: 20px;
      h1{
        font-weight: bold;
        font-size: 17px;
        line-height: 21px;
      }
    }

    &__menu {
      max-width: 558px;
      width: 100%;
      ul {
        display: flex;
        justify-content: space-between;

        li {
          a {
            font-family: 'Gilroy', sans-serif;
            font-weight: bold;
            font-size: 12px;
            line-height: 15px;
            color: #262525;
          }
        }
      }
    }

    &__contact {
      padding-left: 20px;
      h1{
        font-weight: bold;
        font-size: 17px;
        line-height: 21px;
      }
    }
  }
</style>
