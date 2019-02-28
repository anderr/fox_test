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

<style lang="scss">
.card {
	float: left;
	width: 25%;
	text-align: center;
	margin-bottom: 20px;

	@media (max-width: 1000px) {
		width: 33.33%;
	}
	@media (max-width: 800px) {
		width: 50%;
	}
	@media (max-width: 550px) {
		width: 100%;
	}

	&__in {
		display: inline-block;
		background: #FFF;
		border-radius: 7px;
		border: 1px solid #EEE;
		padding: 10px 15px;
		width: 220px;
		box-shadow: 0 2px 43px -4px rgba(0,0,0,.19);
		position: relative;
		cursor: pointer;
		transition: .3s box-shadow, width .3s;

		@media (max-width: 1200px) {
			width: 200px;
		}
		@media (max-width: 1050px) {
			width: 180px;
			font-size: .9em;
		}
		@media (max-width: 1000px) {
			width: 220px;
			font-size: 1em;
		}

		@media (max-width: 940px) {
			width: 200px;
		}
		@media (max-width: 880px) {
			width: 180px;
			font-size: .9em;
		}
		@media (max-width: 800px) {
			width: 220px;
			font-size: 1em;
		}

		@media (max-width: 640px) {
			width: 200px;
		}
		@media (max-width: 600px) {
			width: 180px;
			font-size: .9em;
		}
		@media (max-width: 550px) {
			width: 220px;
			font-size: 1em;
		}

		@media (max-width: 380px) {
			width: 180px;
			font-size: .9em;
		}

		&.clicked {
			background: #EEE;
		}

		&:hover {
			box-shadow: 0 2px 5px rgba(0,0,0,.1), 0 1px 2px rgba(0,0,0,.05);
		}
	}

	&__logoleft {
		position: absolute;
		top: 10px;
		left: 10px;
		width: 50px;
		height: auto;
		pointer-events: none;
	}
	&__logoright {
		position: absolute;
		top: 10px;
		right: 10px;
		width: 50px;
		height: auto;
		pointer-events: none;
	}
	&__logomain {
		width: 160px;
		margin: 20px auto 10px;
		pointer-events: none;
	}
	&__tematic {
		position: relative;
		display: inline-block;
		text-align: left;
		padding-left: 40px;
		max-width: 90%;
		vertical-align: middle;
		font-size: .7em;
		font-weight: bold;
		color: #1D5D1E;
		text-transform: uppercase;
		margin-bottom: 20px;
		pointer-events: none;

		img {
			position: absolute;
			top: 0;
			left: -4px;
			height: 16px;
			width: auto;
		}
		span {
			font-size: 1.4em;
			color: #3CC240;
		}
	}
	&__text {
		font-size: 1.1em;
		padding: 0 5px;
		overflow: hidden;
			display: -webkit-box;
			-webkit-line-clamp: 3;
			-webkit-box-orient: vertical;
			margin-bottom: 10px;
		pointer-events: none;
	}

	&__rating {
		pointer-events: none;
	}

	&__rating-user {
		float: left;
		text-align: left;
		position: absolute;
		left: 10px;
		padding-left: 18px;
		color: #444;
		border-bottom: 1px solid transparent;
		max-width: 6.875em;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
		transition: all .1s;
		pointer-events: auto;

		&:hover {
			color: #111;
			text-decoration: underline !important;
			width: 83%;
			max-width: 83%;
			background: #FFF;
		}

		&:before {
			position: absolute;
			left: 4px;
			top: 5px;
			content: "";
			width: 10px;
			height: 10px;
			background: #CCC;
			box-shadow: 0 0 5px 0 rgba(0,0,0,.2);
			border-radius: 8px;
		}

		&.active {
			&:before {
				background: #44C737;
				box-shadow: 0 0 5px 0 rgba(0,150,0,.5);
			}
		}
	}
	&__rating-rate {
		float: right;
		text-align: right;
		color: #FFA700;
		transition: color .3s;
		pointer-events: none;

		&:hover {
			color: lighten(#FFA700, 17%);
		}
		span {
			color: #CCC;
			font-size: .85em;
		}
	}
	&__rating-hr {
		height: 1px;
		width: 100%;
		margin: 7px auto;
		background: #CCC;
		pointer-events: none;
	}

	&__price {
		pointer-events: none;
	}

	&__price-like {
		float: left;
		color: #CCC;
		font-size: 1.3em;
		transition: color .3s;
		pointer-events: auto;

		i.active {
			color: red;
		}

		&:hover {
			color: red;
		}
	}
	&__price-price {
		float: right;
		font-size: 1.2em;
		font-weight: bold;
		color: #1D5D1E;
		pointer-events: none;
	}
}
</style>
