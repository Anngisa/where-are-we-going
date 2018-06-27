<template>
	<div class="list">
		<li class="item" v-for="item of arr" :key="item" @click="handleLetterClick" :ref="item.toUpperCase()"
		@touchstart="handleTouchStart" 
		@touchmove="handleTouchMove"
		@touchend="handleTouchEnd"
		>
			{{item.toUpperCase()}}
		</li>
	</div>
</template>
<script>
export default{
	name:'CityAlphabet',
	props:{
		cities:Array
	},
	data(){
		return {
			touchStatus:false,
			startY:0,
			timer:null
		}
	},
	updated(){
		this.startY=this.$refs['A'][0].offsetTop
	},
	computed:{
		arr(){
			let tmp=[]
			let allCityList=this.cities
			for(let i=0;i<allCityList.length;i++){
				if(tmp.indexOf(allCityList[i].sortLetters.toLowerCase())==-1){
					tmp.push(allCityList[i].sortLetters.toLowerCase())
				}
			}
			return tmp
		}
	},
	methods:{
		handleLetterClick(e){
			this.$emit('change',e.target.innerText)
		},
		handleTouchStart(){
			this.touchStatus=true
		},
		handleTouchMove(e){
			if(this.touchStatus){
				if(this.timer){
					clearTimeout(this.timer)
				}
				this.timer=setTimeout(()=>{
					const touchY=e.touches[0].clientY-79
					const index=Math.floor((touchY-this.startY)/20)
					if(index>=0&&index<this.arr.length){
						for(let i=0;i<this.arr.length;i++){
							this.$refs[this.arr[i].toUpperCase()][0].style.color="#00bcd4"
						}
						this.$refs[this.arr[index].toUpperCase()][0].style.color='red'
						this.$emit('change',this.arr[index].toUpperCase())
					}
				},16)
			}
		},
		handleTouchEnd(){
			this.touchStatus=false
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