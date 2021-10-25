<template>
	<div>
		<h1>aamir</h1>
		<p>{{todos}}</p>
	</div>
</template>
<script>
export default{
	data(){
		return{
			postId:'',
			todos:''
		}
	},
	methods:{
	async	getPostDetailsById(){
			this.postId = this.$route.query.todo_id;
			this.todos = await this.$axios.$get('https://jsonplaceholder.typicode.com/posts/' + this.postId);

		}

	},

	mounted(){
		this.getPostDetailsById()
	}

};
</script>