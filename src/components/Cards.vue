<template>
	<div>
		<div class="cards cards__main clearfix">
			<transition-group name="list" mode="out-in">
				<card v-for="(cardone, index) in cardsInMain" :key="index" :index="index" :card="card"></card>
			</transition-group>
		</div>
		
		<button class="btn" @click="loadMore" v-if="cardsInMain < maxCardsInMain">Load more...</button>
		<div class="cards__counter">
			Количество карточек: {{ cardsInMain }} (не больше {{ maxCardsInMain }})
		</div>
	</div>
</template>

<script>
	import Card from './Card.vue'

	export default {
		data() {
			return {
				cardsInMain: 4,
				maxCardsInMain: 12
			}	
		},
		props: ['card'],
		methods: {
			loadMore() {
				let step = 4

				if (this.cardsInMain <= this.maxCardsInMain - step) {
					this.cardsInMain += 4;
				} else {
					this.cardsInMain += this.maxCardsInMain - this.cardsInMain;
				}
			}
		},
		components: {
			Card
		}
	}
</script>

<style>
	.list-enter-active, .list-leave-active {
	  transition: all .5s;
	}
	.list-enter, .list-leave-to {
	  opacity: 0;
	  transform: translateY(20px);
	}
</style>