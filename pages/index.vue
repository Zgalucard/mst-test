<template>
  <div class="main">
    <div class="main__container">
      <div class="main__menu">
        <ul>
          <li v-for="item of mainMenuItems" :key="item.id" @click="switchContent(item, item.id)"
              :class="{ 'active-item': activeIndex === item.id }">
            {{ item.item }}
          </li>
        </ul>
      </div>
      <div class="main__content">
        <div class="main__text main__text-alter">
          <transition-group tag="div" name="alt-content" v-if="!alternativeAnimation">
            <h1 :key="currentContentView.title">{{currentContentView.title}}</h1>
            <p :key="currentContentView.text">
              {{currentContentView.text | linkAtTheEnd(110) }}
              <nuxt-link to="/" v-show="currentContentView.text.length > 109">...</nuxt-link>
            </p>
          </transition-group>
          <transition-group tag="div" name="content" v-if="alternativeAnimation">
            <h1 :key="currentContentView.title">{{currentContentView.title}}</h1>
            <p :key="currentContentView.text">
              {{currentContentView.text | linkAtTheEnd(110) }}
              <nuxt-link to="/" v-show="currentContentView.text.length > 109">...</nuxt-link>
            </p>
          </transition-group>
          <div class="main__pages">
            <span>{{ currentContentView.id + 1 }} / {{ mainMenuItems.length }}</span>
          </div>
        </div>
      </div>
      <transition-group tag="div" name="alt-img" class="main__illustration" v-if="!alternativeAnimation">
        <img :key="currentContentView.img" :src="currentContentView.img" alt="">
      </transition-group>
      <transition-group tag="div" name="img" class="main__illustration" v-if="alternativeAnimation">
        <img :key="currentContentView.img" :src="currentContentView.img" alt="">
      </transition-group>
    </div>
  </div>
</template>

<script>
  const mainMenuItem = (id, item) => ({
    id,
    item
  })
  const mainMenuItems = [
    mainMenuItem(0, 'Архитектура'),
    mainMenuItem(1, 'Благоустройство'),
    mainMenuItem(2, 'Безопастность'),
    mainMenuItem(3, 'Инженерия'),
    mainMenuItem(4, 'Инфраструктура'),
    mainMenuItem(5, 'Транспортная доступность')
  ]

  const mainContentItem = (id, title, text, img) => ({
    id,
    title,
    text,
    img
  })
  const mainContentItems = [
    mainContentItem(0,
      'Архитектура',
      'Оригинальная архитектура жилого комплекса бизнес-класса «Первомайская» формирует современный стиль жизни',
      'img/Illustration1.png'
    ),
    mainContentItem(1,
      'Благоустройство',
      'Запроектированные большие окна, которые пропускают много солнечного света, наполнят Ваши квартиры теплотой и уютом',
      'img/Illustration2.png'
    ),
    mainContentItem(2,
      'Безопастность',
      'Современный двор европейского уровня — территория для детей, игр на свежем воздухе и вечерних',
      'img/Illustration3.png'
    ),
    mainContentItem(3,
      'Инженерия',
      'Оригинальная архитектура жилого комплекса бизнес-класса «Первомайская» формирует современный стиль жизни',
      'img/Illustration4.png'
    ),
    mainContentItem(4,
      'Инфраструктура',
      'Прекрасный вариант для тех, кто предпочитает жить в спокойном районе среди интеллигенции, но при этом чувствовать ритм мегаполиса',
      'img/Illustration5.png'
    ),
    mainContentItem(5,
      'Транспортная доступность',
      'Жилой комплекс «Первомайска» расположен в престижном Академическом районе',
      'img/Illustration6.png'
    )
  ]

  export default {
    data() {
      return {
        mainMenuItems: mainMenuItems,
        mainContentItems: mainContentItems,
        currentContentView: mainContentItems[0],
        activeIndex: 0,
        alternativeAnimation: false
      }
    },
    methods: {
      switchContent(item, index) {
        this.currentContentView = mainContentItems[index]
        this.activeIndex = index

      },

      switchAnimation() {
        let mainList = document.querySelectorAll('.main__menu ul li')

        let activeIndex
        let activeItem

        for (const [index, item] of mainList.entries()) {
          if (item.classList.contains('active-item')) {
            activeItem = item
            activeIndex = index
          }

          item.addEventListener('mouseover', (e) => {
            if (activeIndex < index) {
              this.alternativeAnimation = true
              // console.log(this.alternativeAnimation);
            }
            if (activeIndex > index) {
              this.alternativeAnimation = false
              // console.log(this.alternativeAnimation);
            }
          })
        }
      },
    },
    filters: {
      linkAtTheEnd: function (value, length) {
        if (!value) return ''

        return value.length > length ? value.slice(0, length) : value

        // value = value.toString()
        // value = value.slice(-value.length) + '...'
        // return value
      }
    },
    beforeUpdate() {
      this.switchAnimation()
    },
    updated() {
      this.switchAnimation()
    },
    mounted() {
      this.switchAnimation()

      // setInterval(() => console.log(this.alternativeAnimation), 1000)
    }
  }
</script>

<style lang="scss">
  //альтернативаная анимация
  .alt-content-enter-active, .alt-content-leave-active {
    transition: transform .5s, opacity 1s;
  }

  .alt-content-enter, .alt-content-leave-to /* .fade-leave-active до версии 2.1.8 */
  {
    transform: translateY(-50px);
    opacity: 0;
  }

  p.alt-content-leave-active {
    bottom: 0;
  }

  .alt-content-leave-active {
    /*display: none;*/
    transform: translateY(0);
    position: absolute;
    opacity: 0;
  }

  //анимация картинки
  .alt-img-enter-active, .alt-img-leave-active {
    transition: opacity .5s, transform .5s;
  }

  .alt-img-enter /* .fade-leave-active до версии 2.1.8 */
  {
    opacity: 0;
    transform: translateY(100%);
  }

  .alt-img-leave-to {
    /*opacity: 1;*/
  }

  .alt-img-leave-active {
    /*display: none;*/
  }

  //обычная анимация

  .content-enter-active, .content-leave-active {
    transition: transform .5s, opacity 1s;
  }

  .content-enter, .content-leave-to /* .fade-leave-active до версии 2.1.8 */
  {
    transform: translateY(100px);
    opacity: 0;
  }

  p.content-leave-active {
    bottom: 0;
  }

  .content-leave-active {
    /*display: none;*/
    transform: translateY(0);
    position: absolute;
    opacity: 0;
  }

  //анимация картинки через height
  .img-enter-active, .img-leave-active {
    transition: opacity .5s, transform .5s;
  }

  .img-enter /* .fade-leave-active до версии 2.1.8 */
  {
    opacity: 0;
    transform: translateY(-100%);
  }

  .img-leave-to {
    /*opacity: 1;*/
  }

  .img-leave-active {
    /*display: none;*/
  }

  .main {
    width: 100%;

    &__container {
      display: flex;
      height: 100%;
      overflow: hidden;
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

        .active-item {
          font-weight: 700;
          text-transform: uppercase;
          font-size: 14px;

          &::before {
            content: '';
            position: absolute;
            top: 9px;
            left: 0;
            z-index: -1;
            background: #EBD8CC;
            width: 100%;
            height: 9px;
            opacity: 1;
            transition: opacity .5s;
          }
        }

        li {
          padding: 0 4px;
          font-size: 13px;
          cursor: pointer;
          position: relative;
          color: #505050;
          z-index: 1;
          max-width: max-content;

          &::before {
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

          &:hover {
            &::before {
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
      position: relative;

      div {
        position: relative;
      }

      h1 {
        font-size: 44px;
        margin-bottom: 40px;
      }

      p {
        font-size: 18px;
      }

      a {
        width: 28px;
        height: 28px;
        background: #262525;
        color: #fff;
        display: inline-flex;
        justify-content: center;
        margin-left: 7px;
      }

      span {
        font-size: 17px;
      }
    }

    &__pages {
      margin-top: 150px;
    }

    &__illustration {
      position: relative;
      width: 100%;
      height: 100%;

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;

        position: absolute;
        top: 0;
        left: 0;
      }
    }
  }
</style>
