<template>
	<div class="">
			<navBar/>
		
		<div class="container">

			<h1 class="text-primary text-center">{{title}}</h1>


			<div class="col-md-12" v-for="(product,index) in products" :key="index">
				<div v-if="proId == product.productId" class="text-center">
					<img :src="product.image" width="500px" height="500px">
					<h1>{{product.productTitle}}</h1>
				</div>
			</div>
		</div>
	</div>
	

</template>

<script>
export default {

	name: 'details',

	data () {
		return {
			proId:this.$route.params.Pid,
			title:"details",
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
	}
}
</script>

<style lang="css" scoped>
</style>