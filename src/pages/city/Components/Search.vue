<template>
	<div class="search">
		<input type="text" name="" class="search-input" placeholder="输入城市名或拼音">
	</div>
</template>
<script>
export default{
	name:'CitySearch'
}
</script>
<style lang="stylus" scoped>
	@import "~styles/varibles.styl"
	.search
		height:.72rem
		background:$bgColor
		padding:0 .1rem
		.search-input
			width:100%
			height:.62rem
			box-sizing:border-box
			line-height:.62rem
			text-align:center
			border-radius:.06rem
			color:#666
			padding:0 .1rem
</style>