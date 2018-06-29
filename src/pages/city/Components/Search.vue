<template>
<div>
	<div class="search">
		<input type="text" v-model="keyword" name="" class="search-input" placeholder="输入城市名或拼音">
	</div>
	<div class="search-content" ref="search" v-show="keyword">
		<ul>
			<li class="search-item border-bottom" v-for="(item,index) of list" :key="index" @click="handleCityClick(item.name)">{{item.name}}</li>
			<li class="search-item border-bottom" v-show="hasNodata">没有找到匹配数据</li>
		</ul>
	</div>
</div>
</template>
<script>
import BScroll from 'better-scroll';
import {mapMutations} from 'vuex';
export default{
	name:'CitySearch',
	props:{
		cities:Array
	},
	data(){
		return {
			keyword:'',
			list:[],
			timer:null
		}
	},
	methods:{
		handleCityClick(city){
/*				this.$store.commit('changeCity',city)
*/				
				this.changeCity(city)
				this.$router.push('/')
			},
			...mapMutations(['changeCity'])
	},
	computed:{
		hasNodata(){
			return !this.list.length
		}
	},
	watch:{
		keyword(){
			if(this.timer){
				clearTimeout(this.timer)
			}
			if(!this.keyword){
				this.list=[]
				return
			}
			this.timer=setTimeout(()=>{
				const result=[]
				this.cities.forEach((value)=>{
					if(value.spellName.indexOf(this.keyword)>-1||value.name.indexOf(this.keyword)>-1){
						result.push(value)
					}
				})
				this.list=result
			},100)
		}
	},
	mounted(){
		this.scroll=new BScroll(this.$refs.search,{
			click:true 
		})
	}
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
	.search-content
		overflow:hidden
		z-index:1
		position:absolute
		background:#eee
		top:1.58rem
		left:0
		right:0
		bottom:0
		.search-item
			line-height:.62rem
			padding-left:.2rem
			background:#fff
			color:#666
</style>