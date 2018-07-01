<template>
<div>
	<router-link to="/" tag="div" class="header-abs" v-show="showAbs">
			<div class="iconfont header-abs-back">&#xe624;</div>
	</router-link>
	<div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
		经典详情
		<router-link to="/" tag="div" class="header-left">
			<div class="iconfont header-fixed-icon">&#xe624;</div>
		</router-link>
	</div>
</div>	
</template>
<script>
export default{
	name:'detailHeader',
	data(){
		return {
			showAbs:true,
			opacityStyle:{
				opacity:0
			}
		}
	},
	activated(){
		window.addEventListener('scroll',this.handleScroll)
	},
	deactivated(){
		window.removeEventListener('scroll',this.handleScroll)
	},
	methods:{
		handleScroll(){
			const top=document.documentElement.scrollTop
			if(top>60){
				let opacity=top/140
				opacity=opacity>1?1:opacity
				this.opacityStyle={
					opacity
				}
				this.showAbs=false
			}else {
				this.showAbs=true
			}
		}
	}
}
</script>
<style lang="stylus" scoped>
	@import "~styles/varibles.styl"
	.header-abs
		position:absolute
		left:.2rem
		top:.2rem
		width:.8rem
		height:.8rem
		border-radius:.4rem
		text-align:center
		line-height:.8rem
		background:rgba(0,0,0,.8)
		color:#fff
	.header-fixed
		position:fixed
		top:0
		left:0
		right:0 
		height:.86rem
		line-height:.86rem
		text-align:center
		color:#fff
		background:$bgColor
		font-size:.32rem
		.header-left
			width:.64rem
			position:absolute
			top:0
			.header-fixed-icon
				text-align:center
				font-size:.4rem
				color:#fff
</style>