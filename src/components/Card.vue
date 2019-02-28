<template>
	<div class="card" :data-slide="sliderCheck">
		<div class="card__in" @click="clicked($event)">
			<img :src="'img/' + card.logoleft" alt="" class="card__logoleft">
			<img :src="'img/' + card.logomain" alt="" class="card__logomain">
			<img :src="'img/' + card.logoright" alt="" class="card__logoright">

			<div class="card__tematic">
				<img src="img/infinite2.png" alt="" class="card__infinite">
				<span>100%</span> Тематические форумы<br>Ручное размещение
			</div>

			<div class="card__text">{{ card.lorem }}</div>

			<div class="card__rating clearfix">
				<div class="card__rating-user" :class="{active: index == 2 || index == 0}">
					{{ card.user }}
				</div>
				<div class="card__rating-rate">
					<i class="icon-star"></i> 5.0 <span>(260)</span>
				</div>
			</div>
			<div class="card__rating-hr"></div>
			<div class="card__price clearfix">
				<div class="card__price-like">
					<i class="icon-heart" @click.stop="like($event)"></i>
				</div>
				<div class="card__price-price">
					от 500 <span class="rouble">Р</span>
				</div>
			</div> 
		</div>
	</div>
</template>

<script>
	export default {
		props: ['card', 'index', 'slider'],
		methods: {
			// Методы клика по карточке и клика по лайку (сердцу)
			clicked(event) {
				if (event.target.classList.contains('clicked')) {
					event.target.classList.remove("clicked");
				} else {
					event.target.classList.add("clicked");
					
					// можно делать редирект на нужную страницу, чтобы сохранить валидность w3c страницы
					console.log('redirect to?');
				}

			},
			like(event) {
				if (event.target.classList.contains('active')) {
					event.target.classList.remove("active");
				} else {
					event.target.classList.add("active");
				}
			},
		},
		computed: {
			sliderCheck() {
				if (this.slider) {
					return this.index;
				}
			}
		}
	}
</script>