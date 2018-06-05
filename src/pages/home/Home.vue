<template>
	<div >
		<home-header></home-header>
		<home-swiper></home-swiper>
		<div>text</div>
	</div>
</template>

<script>
	import HomeHeader from './Components/Header'
	import HomeSwiper from './Components/Swiper'
	export default {
		name:'Home',
		components:{
			HomeHeader,
			HomeSwiper
		}
	}
</script>
<style >
	
</style>