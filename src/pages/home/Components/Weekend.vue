<template>
	<div>
		<div class="title">周末去哪</div>
		<ul>
			<li class="item border-bottom" v-for="item of recommendList" :key="item.id">
				<div class="item-img-wrapper">
					<img class="item-img" :src="item.imgUrl"/>
				</div>
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
				</div>
				
			</li>
		</ul>
	</div>
</template>
<script >
	export default{
		name:'HomeWeekend',
		data(){
			return {
				recommendList:[
					{id:"001",imgUrl:"http://img1.qunarzz.com/sight/source/1505/4e/3e87ee62e59cdb.jpg_r_640x214_fe6cc902.jpg",title:"杭州必游TOP10",desc:"杭州，前世今生与你有一场美丽约会"},
					{id:"002",imgUrl:"http://img1.qunarzz.com/sight/source/1505/9f/7d45cc38259e0.jpg_r_640x214_156f4299.jpg",title:"承载杭城的历史之地",desc:"饱经沧桑的地方诉述着这座城的段段衷肠"}, 
					{id:"003",imgUrl:"http://img1.qunarzz.com/sight/source/1505/bc/83feb2e003d0dd.jpg_r_640x214_0b7269b8.jpg",title:"杭州多样乐园",desc:"这个周末终于可以陪宝贝去玩耍啦"}
				]
			}
			
		}
	}
</script>
<style lang="stylus" scoped>
	@import "~styles/mixin.styl"
	.title
		line-height:.8rem
		background:#eee
		text-indent:.2rem
		font-size:.32rem
	.item-img-wrapper
		height:0
		padding-bottom:37.4375%
		overflow:hidden
		.item-img
			display:inline-block
			width:100%
	.item-info
		position:relative
		padding:.14rem .2rem .2rem .2rem
		.item-title
			padding-right:1.4rem
			font-size:.28rem
			line-height:.48rem
			color:#212121
			ellipise()
		.item-desc
			padding-right:1.4rem
			color:#616161
			font-size:.24rem
			
		
</style>