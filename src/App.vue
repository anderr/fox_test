<template>
  <div id="app" class="page">
  <div class="page__content">
    <TheHeader />

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
  import TheHeader from './components/TheHeader.vue'
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
      appSlider: Slider,
      TheHeader,
    }
  }
</script>

<style lang="scss">
html {
	height: 100%;
}
body {
	background: #F4F4F4;
	height: 100%;
	font-family: 'Cuprum', sans-serif;
}
img {
	display: block;
}

.page {
	display: flex;
	flex-direction: column;
	height: 100%;

	&__content {
		flex: 1 0 auto;
	}
	&__footer {
		flex: 0 0 auto;
		text-align: center;
		padding: 20px;
		border-top: 1px solid #DDD;
		font-size: .75em;
		color: #333;

		a {
			color: #333;
			text-decoration: none;
			border-bottom: 1px solid transparent;
			transition: .3s all;

			&:hover {
				color: #111;
				border-bottom: 1px solid #111;
			}
		}
	}
}

.container {
	max-width: 1200px;
	padding: 0 30px;
	margin: 0 auto;
	position: relative;
}

.rouble {
	position: relative;

	&:after {
		content: "–";
		position: absolute;
		bottom: -.15em;
		left: -.05em;
	}
}

.clearfix:after {
  content: "";
  display: table;
  clear: both;
}

.btn {
	float: none;
	display: block;
	background: #FFF;
	border: 1px solid #BBB;
	border-radius: 4px;
	width: 220px;
	margin: 10px auto;
	text-align: center;
	line-height: 40px;
	font-weight: bold;
	color: #666;
	cursor: pointer;
	outline: none;
	transition: background .3s;

	&:hover {
		background: darken(#FFF, 5%);
	}
}

.rotate180 {
	transform: rotate(180deg);
}

</style>
