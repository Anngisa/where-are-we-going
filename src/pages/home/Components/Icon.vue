<template>
	<div class="icons">
	 	<swiper>
	    <swiper-slide v-for="(page,index) of pages" :key="index">
	    	<div class="icon" v-for="item of page" :key=item.id>
					<div class="icon-img">
						<img class="icon-img-content" :src="item.imgUrl">
					</div>
					<p class="icon-desc">{{item.desc}}</p>
				</div>
	    </swiper-slide>
	    <div class="swiper-pagination"  slot="pagination"></div>
	  </swiper>
		

	</div>
</template>
<script >
	export default{
		name:"HomeIcons",
		props:{
			iconList:Array
		},
		computed:{
			pages(){
				const pages=[]
				this.iconList.forEach((item,index)=>{
					const page=Math.floor(index/8)
					if(!pages[page]){
						pages[page]=[]
					}
					pages[page].push(item)
				})
				return pages
			}
		}

	}
</script>
<style lang="stylus" scoped>
	@import "~styles/varibles.styl"
	@import "~styles/mixin.styl"
	
	.icons>>>.swiper-container
		height:3.7rem
		padding-top:.2rem
		box-sizing:border-box
	.icons
		width:100%
		overflow:hidden
		.icon
			position:relative
			float:left
			width:25%
			height:1.5rem
			padding-top:.1rem
			overflow:hidden
			text-align:center
			.icon-img
				display:inline-block
				width:1.1rem
				height:1.1rem
				.icon-img-content
					display:block
					height:100%
			.icon-desc
				position:absolute
				bottom:0
				left:0
				right:0
				line-height:.44rem
				height:.44rem 
				color:$darkStyleColor
				text-align:center
				ellipsis()
</style>