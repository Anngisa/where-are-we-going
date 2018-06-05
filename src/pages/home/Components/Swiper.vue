<template>
	<div class="wrapper">
		 <swiper :options="swiperOption">
	    <swiper-slide v-for="item of swiperOption.swiperList" :key=item.id>
	    	<img class="swiper-img" :src="item.imgUrl">
	    </swiper-slide>
	    <div class="swiper-pagination"  slot="pagination"></div>
	  </swiper>
  </div>
</template>
<script>
export default{
	name:'HomeSwiper',
 	data() {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination',
        },
        loop:true,
        swiperList:[
        	{id:'0001',imgUrl:'http://img1.qunarzz.com/piao/fusion/1609/f8/ef0b29100632f002.jpg_750x200_ebe20c8f.jpg'},
        	{id:'002',imgUrl:'http://img1.qunarzz.com/piao/fusion/1806/8b/2680212fadf30002.jpg_750x200_f85409ac.jpg'}]
      }
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