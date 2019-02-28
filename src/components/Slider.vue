<template>
	<div>
		<div class="cards cards__slider clearfix">
			<div
				class="cards__slider-arrow cards__slider-left"
				:class="disableLeftArrow"
				@click="prevSlide"
				v-if="cardsInSlider > slidesPerRow">
				<i class="icon-arrow-left"></i>
			</div>

			<div id="slider-track">
				<div class="slider-track-inner" :style="{width: computedTrackWidth}" :class="centered">
					<card
						v-for="(cardone, index) in cardsInSlider"
						:key="index"
						:index="index"
						:card="card"
						:slider="slider"
						:style="{width: computedSlideWidth}">
					</card>
				</div>
			</div>

			<div
				class="cards__slider-arrow cards__slider-right"
				:class="disableRightArrow"
				@click="nextSlide"
				v-if="cardsInSlider > slidesPerRow">
				<i class="icon-arrow-right"></i>
			</div>
		</div>
		
		<button class="btn" @click="appendSlide" v-if="cardsInSlider < 5">Добавить слайд</button>
		<div class="cards__counter">{{ cardsInSlider }} из возможных {{ maxCardsInSlider }}</div>
	</div>
</template>

<script>
	import Card from './Card.vue'

	export default {
		data() {
			return {
				cardsInSlider: 2,
				maxCardsInSlider: 12,
				slider: true,
				currentSlide: 0,
				transform: 0,
				slidesPerRow: 4,
				windowWidth: 0
			}	
		},
		props: ['card'],
		methods: {
			nextSlide() {
				if (this.currentSlide < this.cardsInSlider - this.slidesPerRow) {
					let track = document.getElementById('slider-track').getElementsByClassName('slider-track-inner')[0];
					let trackWidth = track.offsetWidth;

					this.currentSlide++;

					this.transform = this.transform - (trackWidth / this.cardsInSlider);
					track.style.transform = 'translateX(' + this.transform + 'px)';
					
					this.appendSlide();
				}
			},
			prevSlide() {
				if (this.currentSlide > 0) {
					let track = document.getElementById('slider-track').getElementsByClassName('slider-track-inner')[0];
					let trackWidth = track.offsetWidth;

					this.currentSlide--;

					this.transform = this.transform + (trackWidth / this.cardsInSlider);

					track.style.transform = 'translateX(' + this.transform + 'px)';
				}
			},
			getWindowWidth(event) {
	        	this.windowWidth = screen.width;

	        	if (this.windowWidth > 1000) {
	        		this.slidesPerRow = 4;
	        	} else if (this.windowWidth <= 1000 && this.windowWidth > 800) {
	        		this.slidesPerRow = 3;
	        	} else if (this.windowWidth <= 800 && this.windowWidth > 550) {
	        		this.slidesPerRow = 2;
	        	} else if (this.windowWidth <= 550) {
	        		this.slidesPerRow = 1;
	        	}
	    	},
	    	appendSlide() {
	    		// добавляем новый слайдер после нажатия кнопки next при условии что не достигнуто максимальное количество элементов в слайдере
				if (this.cardsInSlider < this.maxCardsInSlider) {
					this.cardsInSlider++;
				}
	    	},
		},
		computed: {
			centered() {
				if (this.cardsInSlider < this.slidesPerRow) {
					return 'centered';
				}
			},
			computedTrackWidth() {
				if (this.cardsInSlider > this.slidesPerRow) {
					return this.cardsInSlider * (100 / this.slidesPerRow) + '%';
				} else {
					return '100%';
				}
			},
			computedSlideWidth() {
				return 100 / this.cardsInSlider + '%';
			},
			disableRightArrow() {
				if (this.currentSlide == this.cardsInSlider - this.slidesPerRow) {
					return 'cards__slider-disabled';
				}
			},
			disableLeftArrow() {
				if (this.currentSlide == 0) {
					return 'cards__slider-disabled';
				}
			},
		},
		components: {
			Card
		},
		mounted() {
			window.addEventListener('resize', this.getWindowWidth);

			this.getWindowWidth();
		},
		beforeDestroy() {
		    window.removeEventListener('resize', this.getWindowWidth);
		}
	}
</script>