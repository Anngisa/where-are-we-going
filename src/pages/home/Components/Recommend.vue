<template>
	<div>
		<div class="title">猜你喜欢</div>
		<ul>
			<router-link  
				tag="li" 
				class="item border-bottom" 
				v-for="item of List" 
				:key="item.id"
				:to="'/detail/'+item.id"
			>
				<img class="item-img" :src="item.imgUrl"/>
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
					<p class="item-price"><span>￥</span><em class="mpg-price-num">{{item.price}}</em>起</p>
				</div>
			</router-link>
		</ul>
	</div>
</template>
<script >
	export default{
		name:'HomeRecommend',
		props:{
			List:Array
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
	.item
		overflow:hidden
		display:flex
		height:1.9rem
		padding:.2rem 0
		.item-img
			display:inline-block
			width:2rem
			height:2rem
			padding:0 .2rem
		.item-info
			flex:1	
			min-width:0
			.item-title
				line-height:.54rem
				font-size:.32rem
				ellipsis()
			.item-desc
				line-height:.4rem
				color:#ccc
				ellipsis()
			.item-price
				line-height:.44rem
				margin-top:.26rem
				border-radius:.1rem
				line-height:.50rem
				span
					color:#ff8300
				.mpg-price-num
					color:#ff8300
					font-size:.4rem
				
</style>