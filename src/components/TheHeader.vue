<template lang="html">
  <div>
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
  </div>
</template>

<script>
export default {
}
</script>

<style lang="scss" scoped>
.header {
	border-bottom: 1px solid #DDD;
	padding: 7px 10px;

	.container {
		align-content: center;
		align-items: center;
		display: flex;
		flex-wrap: nowrap;
		flex-direction: row;
		justify-content: space-between;

		padding: 0 10px;
	}

	&__logo {
		flex: 0 1 auto;

		height: 38px;

		img {
			height: 100%;
			width: auto;
		}
	}
	&__text {
		flex: 0 1 auto;

		font-size: 1.2em;
		text-align: center;
	}
	&__menu {
		i {
			font-size: 1.6em;
			color: #AAA;
			cursor: pointer;
			transition: .3s color;

			&:hover {
				color: #111;
			}
		}
	}
}
</style>
