<template>
	<div class="list">
		<li class="item" v-for="(item,index) of arr" :key="index">{{item.toUpperCase()}}</li>
	</div>
</template>
<script>
export default{
	name:'CityAlphabet',
	props:{
		cities:Array
	},
	computed:{
		arr(){
			let tmp=[]
			var allCityList=this.cities
			for(var i=0;i<allCityList.length;i++){
				if(tmp.indexOf(allCityList[i].sortLetters.toLowerCase())==-1){
					tmp.push(allCityList[i].sortLetters.toLowerCase())
				}
			}
			return tmp
		}
		
	}
}
</script>
<style lang="stylus" scoped>
	@import "~styles/varibles.styl"
	.list
		display:flex
		flex-direction:column
		justify-content:center
		position:absolute
		top:1.58rem
		right:0
		bottom:0
		width:.4rem
		.item
			line-height:.4rem
			color:$bgColor
			text-align:center
</style>