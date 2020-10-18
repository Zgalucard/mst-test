<template>
  <div class="footer">
    <div class="footer__container">
      <div class="footer__text">
        <h1>Разработано в MST</h1><h1>|</h1><h1>2018</h1>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'BottomBar',
  }
</script>

<style scoped lang="scss">
  .footer {
    max-width: 1920px;
    width: 100%;
    height: 60px;
    background: #fff;

    text-transform: uppercase;
    &__container {
      width: 100%;
      margin: 0 auto;
      display: flex;
      align-items: center;
      height: 100%;
      justify-content: space-between;
    }

    &__text{
      display: flex;
      min-width: 205px;
      justify-content: space-between;

      h1{
        font-weight: 300;
        font-size: 13px;
        line-height: 15px;
      }
    }
  }
</style>
