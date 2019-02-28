<template>
  <div id="app" class="page">
  <div class="page__content">
    <div class="header">
      <div class="container">
        <a href="/" class="header__logo">
          <img src="img/logo.png" alt="">
        </a>
        <div class="header__text">
          Список карточек
        </div>
        <div class="header__menu">
          <i class="icon-menu"></i>
        </div>
      </div>
    </div>
    
    <div class="container">
      <app-cards :card="card"></app-cards>
      <app-slider :card="card"></app-slider>
    </div>
  </div>

    <div id="footer" class="page__footer">
      © 2018 <a href="http://mirafox.com">Mirafox</a>
    </div>
  </div>
</template>

<script>
  import Cards from './components/Cards.vue'
  import Slider from './components/Slider.vue'

  export default {
    data() {
      return {
        card: {
          logoleft: 'natural1.png',
          logomain: 'juicy_links.png',
          logoright: 'natural2.png',
          lorem: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consectetur assumenda vitae quasi! Quos adipisci iusto maxime officiis consequatur id veniam.',
          user: 'userName userName user'
        },
      }
    },
    components: {
      appCards: Cards,
      appSlider: Slider
    }
  }
</script>
