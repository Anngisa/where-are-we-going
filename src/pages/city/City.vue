<template>
	<div>
		<city-header></city-header>
		<city-search></city-search>
		<city-list :cities="cities" :hot="hotCities" :letter="letter"></city-list>
		<city-alphabet :cities="cities" @change="handleLetterChange"></city-alphabet>
	</div>
</template>
<script>
import axios from 'axios'
import CityHeader from './Components/Header.vue'	
import CitySearch from './Components/Search.vue'
import CityList from './Components/List.vue'
import CityAlphabet from './Components/Alphabet.vue'

export default{
	name:'City',
	components:{
		CityHeader,
		CitySearch,
		CityList,
		CityAlphabet
	},
	data(){
		return {
			cities:[],
			hotCities:[],
			letter:''
		}
	},
	methods:{
		getCityInfo(){
			axios.get('/api/city.json').then(this.handleGetCityInfoSucc)
		},
		handleGetCityInfoSucc(res){
			res=res.data
			if(res.ret&&res.data){
				const data=res.data
				this.cities=data.allCityList
				this.hotCities=data.hotCities
				console.log(typeof this.hotCities)
			}
		},
		handleLetterChange(letter){
			this.letter=letter
		}
	},
	mounted(){
		this.getCityInfo()
	}
}
</script>
<style lang="stylus">
	
</style>