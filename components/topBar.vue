<template>
  <div class="header">
    <div class="header__container">
      <div class="header__logo">
        <h1>Первомайская</h1>
      </div>
      <div class="header__menu">
        <ul>
          <div class="header__line"></div>
          <li>
            <nuxt-link exact active-class="active-link" to="/">О комплексе</nuxt-link>
          </li>
          <li>
            <nuxt-link active-class="active-link" to="/features">Особенности</nuxt-link>
          </li>
          <li>
            <nuxt-link active-class="active-link" to="/penthouses">Пентхаусы</nuxt-link>
          </li>
          <li>
            <nuxt-link active-class="active-link" to="/apartments">Выбрать квартиру</nuxt-link>
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
    name: 'topbar',
    data() {
      return {}
    },
    methods: {
      // headerUnderline() {
      //   let headerEl = document.querySelectorAll('.header__menu ul li a')
      //   // console.log(headerEl)
      //   let line = document.querySelector('.header__line')
      //
      //   let activeIndex
      //   let activeItem
      //
      //   for (const [index, item] of headerEl.entries()) {
      //     if (item.classList.contains('active-link')) {
      //       activeItem = item
      //       activeIndex = index
      //       line.style.left = '' + 25 * (activeIndex + 1) + '%';
      //     }
      //   }
      //
      //   let smActive = []
      //   let bgActive = []
      //
      //   for (const [index, item] of headerEl.entries()) {
      //     // console.log(index, item)
      //     if (activeIndex < index) {
      //       bgActive.push(index)
      //
      //       for (const [bgInd, bgIt] of bgActive.entries()) {
      //         item.addEventListener('mouseover', function (e) {
      //           // console.log(item)
      //           //                item.classList.add('active-hover')
      //           line.style.width = '' + 25 * (bgInd + 1) + '%';
      //         })
      //       }
      //     }
      //     if (activeIndex > index) {
      //       smActive.push(index)
      //
      //       for (const [smInd, smIt] of smActive.entries()) {
      //         item.addEventListener('mouseover', function (e) {
      //           //                item.classList.add('active-hover')
      //           line.style.width = '' + 25 * (smInd + 1) + '%';
      //           line.style.left = '' + 25 * (smInd) + '%';
      //           if (smInd === 0) {
      //             line.style.width = '' + 25 * (smInd + 3) + '%';
      //           }
      //         })
      //       }
      //     }
      //
      //     item.addEventListener('mouseout', function (e) {
      //       //                item.classList.add('active-hover')
      //       line.style.width = '' + 0 + '%';
      //       line.style.left = '' + 25 * (activeIndex + 1) + '%';
      //     })
      //   }
      // }
    },
    mounted() {
      // this.headerUnderline()
    }
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

      h1 {
        font-weight: bold;
        font-size: 17px;
        line-height: 21px;
      }
    }

    .active-link {
      &::before {
        content: '';
        position: absolute;
        width: 100%;
        height: 4px;
        background: #D88F5E;
        bottom: -7px;
        left: 0;
      }
    }

    &__line {
      position: absolute;
      height: 4px;
      width: 0%;
      background: #D88F5E;
      bottom: -7px;
      left: 0;

      transition: width .2s ease-out, left .2s ease-out;
    }

    &__menu {
      max-width: 558px;
      width: 100%;

      ul {
        display: flex;
        justify-content: space-between;
        position: relative;

        li {
          display: flex;
          flex: 0 0 25%;
          justify-content: center;
          position: relative;

          a {
            position: relative;
            font-family: 'Gilroy', sans-serif;
            font-weight: bold;
            font-size: 12px;
            line-height: 15px;
            color: #262525;
            padding: 0 6px;
          }
        }
      }
    }

    &__contact {
      padding-left: 20px;

      h1 {
        font-weight: bold;
        font-size: 17px;
        line-height: 21px;
      }
    }
  }
</style>
