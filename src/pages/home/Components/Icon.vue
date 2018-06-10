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
		name:'HomeIcons',
		data(){
			return {
				iconList:[
				{id:'0001',imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',desc:'景点门票'},
				{id:'0002',imgUrl:'http://img1.qunarzz.com/piao/fusion/1804/ed/cf572be30fc32f02.png',desc:'Q+精选'},
				{id:'0003',imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/47/c2b659e048b11602.png',desc:'主题乐园'},
				{id:'0004',imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/75/eca3ce656c886502.png',desc:'漂流'},
				{id:'0005',imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/50/26ffa31b56646402.png',desc:'亲子游'},
				{id:'0006',imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/17/99402a22ce4af302.png',desc:'印象西湖'},
				{id:'0007',imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/e3/67df61427c8e1302.png',desc:'宋城千古情'},
				{id:'0008',imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/b8/c5dcdb58deec2402.png',desc:'西溪湿地'},
				{id:'0009',imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/75/eca3ce656c886502.png',desc:'千岛湖'},
				{id:'0010',imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/80/416c6ab3368d1f02.png',desc:'全部游玩'},

				]
			}
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