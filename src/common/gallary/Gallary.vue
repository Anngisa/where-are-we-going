<template>
	<div class="container" @click="handleGallaryClick">
		<div class="wrapper">
			<swiper :options="swiperOption">
		    <swiper-slide v-for="(item,index) in imgs" :key="index">
		    	<img class="gallary-img" :src="item">
		    </swiper-slide>
		    <div class="swiper-pagination"  slot="pagination"></div>
		  </swiper>
		</div>
	</div>
</template>
<script>
	export default{
		name:'commomGallary',
		props:{
			imgs:{
				type:Array,
				default(){
					return []
				}
			}
		},
		data(){
			return {
				swiperOption:{
					pagination: {
	        	el: '.swiper-pagination',
	        	type:'fraction'
	        },
	        observer:true,
   				observeParents:true,
				}
			}
		},
		methods:{
			handleGallaryClick(){
				this.$emit('close')
			}
		}
	}
</script>
<style lang="stylus" scoped>
	.container>>>.swiper-container 
		overflow:inherit
	.container
		position:fixed
		display:flex
		flex-direction:column
		justify-content:center
		left:0
		top:0
		right:0
		bottom:0
		background:#000
		z-index:99
		.wrapper
			width:100%
			height:0
			padding-bottom:100%
			.gallary-img
				width:100%
			.swiper-pagination
				color:#fff
				bottom:-1rem
</style>