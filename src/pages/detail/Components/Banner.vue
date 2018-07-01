<template>
<div>
	<div class="banner" @click="handleBannerClick">
		<img class="banner-img" :src="bannerImg">
		<div class="banner-info">
			<div class="banner-number"><span class="iconfont banner-icon">&#xe608;</span>{{this.bannerImgs.length}}</div>
			<div class="banner-title">{{this.sightName}}</div>
		</div>
	</div>
	<common-gallary :imgs="bannerImgs" v-show="showGallary" @close="handleGalleryClose"></common-gallary>
</div>	
</template>
<script>
import commonGallary from 'common/gallary/Gallary';
export default{
	name:'detailBanner',
	components:{
		commonGallary
	},
	props:{
		sightName:String,
		bannerImg:String,
		bannerImgs:Array
	},
	data(){
		return {
			showGallary:false
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