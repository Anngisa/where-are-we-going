<template>
	<div>
		<div class="title">周末去哪</div>
		<ul>
			<li class="item border-bottom" v-for="item of List" :key="item.id">
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