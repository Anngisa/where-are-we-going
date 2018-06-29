<template>
	<div >
		<home-header></home-header>
		<home-swiper :swiperList="swiperList"></home-swiper>
		<home-icons :iconList="iconList"></home-icons>
		<home-recommend :List="recommendList"></home-recommend>
		<home-weekend :List="weekendList"></home-weekend>
	</div>
</template>

<script>
	import HomeHeader from './Components/Header'
	import HomeSwiper from './Components/Swiper'
	import HomeIcons from './Components/Icon'
	import HomeRecommend from './Components/Recommend'
	import HomecenterSwiper from './Components/centerSwiper'
	import HomeWeekend from './Components/Weekend'
	import axios from 'axios'
	export default {
		name:'Home',
		components:{
			HomeHeader,
			HomeSwiper,
			HomeIcons,
			HomecenterSwiper,
			HomeRecommend,
			HomeWeekend
		},
		data(){
			return {
				swiperList:[],
				iconList:[],
				recommendList:[],
				weekendList:[]
			}
		},
		mounted(){
			this.getHomeInfo()
		},
		methods:{
			getHomeInfo(){
				axios.get('/api/index.json').then((res)=>{
					res=res.data
					if(res.ret&&res.data){
						const data=res.data
						this.swiperList=data.swiperList
						this.iconList=data.iconList
						this.recommendList=data.recommendList
						this.weekendList=data.weekendList
					}
				})
			},
			
		}
	}
</script>
<style >
	
</style>