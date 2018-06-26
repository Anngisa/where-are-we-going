<template>
	<div class="list" ref="wrapperList">
	<div>
			<div class="area">
				<div class="title border-topbottom">当前城市</div>
				<div class="button-list">
					<div class="button-wrapper">
						<div class="button">北京</div>
					</div>
				</div>
			</div>
			<div class="area">
				<div class="title border-topbottom">热门城市</div>
				<div class="button-list">
					<div class="button-wrapper" v-for="item of hot" :key="item.id">
						<div class="button">{{item.name}}</div>
					</div>
				</div>
			</div>
			<div class="area" v-for="(item,key) of json">
				<div class="title border-topbottom">{{key.toUpperCase()}}</div>
				<div class="item-list">
					<div class="item border-bottom" v-for="innerItem of item" :key="innerItem.id">
						{{innerItem.name}}
					</div>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
	import BScroll from 'better-scroll';
	export default{
		name:'CityList',
		data(){
			return {
				jsont:{}
			}
		},
		props:{
			hot:Array,
			cities:Array
		}, 
		methods:{

		},
		computed:{
			json:function(){
				let jsont={}
				let allCityList=this.cities
				let arr=[]
				for(var i=0;i<allCityList.length;i++){
					if(arr.indexOf(allCityList[i].sortLetters.toLowerCase())==-1){
						arr.push(allCityList[i].sortLetters.toLowerCase())
					}
				}
				for(var j=0;j<arr.length;j++){
					let key=arr[j]
					jsont[key]=[]
					for(var xx=0;xx<allCityList.length;xx++){
						if(key==allCityList[xx].sortLetters){
							jsont[key].push(allCityList[xx])
						}
					}
				}
				return jsont
			}	
		},
		mounted(){
			this.scroll=new BScroll(this.$refs.wrapperList,{
				click:true,
			})

		}
	}
</script>
<style lang="stylus" scoped>
	@import "~styles/varibles.styl"
	.list
		position:absolute
		top:1.58rem
		left:0
		right:0
		bottom:0
		overflow:hidden
		.title
			line-height:.4rem
			background:#eee
			padding-left:.2rem
			font-size:.26rem
		.border-topbottom
			&:before
				background:#ccc
			&:after
				background:#ccc
		.button-list
			padding:.1rem
			overflow:hidden
			pading:.1rem .6rem .1rem .1rem
			.button-wrapper
				width:33.33%
				float:left
				.button
					text-align:center
					padding:.1rem 0
					margin:.1rem
					border:.02rem solid #ccc
					border-radius:.06rem 
		.item-list
			.item
				line-height:.76rem
				padding-left:.2rem
				.border-bottom
					&:before
						background:#ccc
</style>