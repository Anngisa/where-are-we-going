<template>
	<div class="wrapper">
		 <swiper :options="swiperOption" v-if="showSwiper">
	    <swiper-slide v-for="item of swiperList" :key=item.id>
	    	<img class="swiper-img" :src="item.imgUrl">
	    </swiper-slide>
	    <div class="swiper-pagination"  slot="pagination"></div>
	  </swiper>
  </div>
</template>
<script>
export default{
	name:'HomeSwiper',
	props:{
		swiperList:Array
	},
 	data() {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination',
        },
        loop:true,

      }
    }
  },
  computed:{
  	showSwiper(){
  		return this.swiperList.length
  	}
  }
}
</script>
<style lang="stylus" scoped>
	.wrapper >>>.swiper-pagination-bullet-active
		background:#fff !important
	.wrapper
		width:100%
		height:0
		overflow:hidden
		background:#fff
		padding-bottom:26.66%
		.swiper-img
			width:100%
</style>