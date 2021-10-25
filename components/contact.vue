<template>
	<div>
		<navBar/>
		<div class="container text-center">
			<h1 class="my-5 text-info">Contact Us Page</h1>
			<div class="row">
				<div class="col-md-3 col-lg-4" v-for="(data,index) in products" :key="index" >
					<img :src="data.image" width="250px" height="250px">
					<h3 @click="goToDetails(data.productId)">{{data.productTitle}}</h3>
				</div>
			</div>
		</div>

	</div>	
</template>

<script>
export default {

	name: 'contact',

	data () {
		return {
			products:[
			{
				productTitle:"Picture 1",
				image       : require('~/assets/images1.jpg'),
				productId:1
			},
			{
				productTitle:"Picture 2",
				image       : require('~/assets/images2.jpg'),
				productId:2
			},
			{
				productTitle:"Picture 3",
				image       : require('~/assets/images3.jpg'),
				productId:3
			},
			{
				productTitle:"Picture 4",
				image       : require('~/assets/images6.jpg'),
				productId:4
			},
			{
				productTitle:"Picture 5",
				image       : require('~/assets/images4.jpg'),
				productId:5
			},
			{
				productTitle:"Picture 6",
				image       : require('~/assets/images5.jpg'),
				productId:6
			}
			]


		}
	},
	methods:{
		goToDetails(prodId){
			this.$router.push({name:'details',params:{Pid:prodId}})
		}
	}
}
</script>

<style lang="css" scoped>
</style>