<template>
	<div >
		<home-header></home-header>
		<home-swiper></home-swiper>
		<home-icons></home-icons>
		<home-recommend></home-recommend>
		<home-weekend></home-weekend>
	</div>
</template>

<script>
	import HomeHeader from './Components/Header'
	import HomeSwiper from './Components/Swiper'
	import HomeIcons from './Components/Icon'
	import HomeRecommend from './Components/Recommend'
	import HomecenterSwiper from './Components/centerSwiper'
	import HomeWeekend from './Components/Weekend'
	export default {
		name:'Home',
		components:{
			HomeHeader,
			HomeSwiper,
			HomeIcons,
			HomecenterSwiper,
			HomeRecommend,
			HomeWeekend
		}
	}
</script>
<style >
	
</style>