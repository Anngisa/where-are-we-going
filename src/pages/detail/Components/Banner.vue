<template>
<div>
	<div class="banner" @click="handleBannerClick">
		<img class="banner-img" src="http://img1.qunarzz.com/sight/p0/1508/12/4e6170303c63bdb7070fb1987480afab.water.jpg_600x330_8db91d9d.jpg">
		<div class="banner-info">
			<div class="banner-number"><span class="iconfont banner-icon">&#xe608;</span>11</div>
			<div class="banner-title">杭州烂苹果乐园</div>
		</div>
	</div>
	<common-gallary :imgs="imgs" v-show="showGallary" @close="handleGalleryClose"></common-gallary>
</div>	
</template>
<script>
import commonGallary from 'common/gallary/Gallary';
export default{
	name:'detailBanner',
	components:{
		commonGallary
	},
	data(){
		return {
			showGallary:false,
			imgs:['http://img1.qunarzz.com/sight/p0/201403/07/0a7decf6c090404c1663ab2c88d69189.jpg_r_800x800_1cf71f86.jpg','http://img1.qunarzz.com/sight/p0/1508/12/4e6170303c63bdb7070fb1987480afab.water.jpg_r_800x800_d178ce8b.jpg']
		}
		
	},
	methods:{
		handleBannerClick(){
			this.showGallary=true;
		},
		handleGalleryClose(){
			this.showGallary=false
		}
	}
}
</script>
<style lang="stylus" scoped>
	.banner
		position:relative
		overflow: hidden
		width:100%
		height:0
		padding-bottom:55%
		.banner-img
			width:100%
		.banner-info
			position:absolute
			bottom:0
			left:.2rem
			right:0
			background-image:linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8))
			.banner-number
				height:.4rem
				width:1.2rem
				background:rgba(0,0,0,.5)
				border-radius:.2rem
				font-size:.24rem
				line-height:.4rem
				text-align:center
				color:#fff
				padding-bottom:.20rem
				.banner-icon
					font-size:.24rem
			.banner-title
				min-height:.4rem
				color:#fff
				margin-bottom:.3rem
</style>