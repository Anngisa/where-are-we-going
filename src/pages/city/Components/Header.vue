<template>
	<div class="header">
		<router-link to="/">
			<div class="header-left"><div class="iconfont back-icon">&#xe624;</div></div>
		</router-link>
		城市选择
	</div>
</template>
<script>
export default{
	name:'CityHeader'
}
</script>
<style lang="stylus" scoped>
	@import "~styles/varibles.styl"
	.header
		position:relative
		height:.86rem
		line-height:.86rem
		overflow:hidden
		text-align:center
		color:#fff
		background:$bgColor
		font-size:.32rem
		.header-left
			width:.64rem
			position:absolute
			.back-icon
				text-align:center
				font-size:.4rem
				color:#fff
</style>