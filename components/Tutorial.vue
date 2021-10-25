<!-- Please remove this file from your project -->
<template>
  <div class="">
    <div class="container">

      <div>

        <b-modal ref="my-modal" hide-footer>
          <template #modal-title>
            Edit Post
          </template>
          <div class="">
            <form>
              <div class="">
                <label for="title">Post Title</label>
                <input type="text" v-model="editForm.title" class="form-control" id="title" placeholder="title">
              </div>
              <div>
                <label for="body">Post Details</label>
                <input type="text" v-model="editForm.Body" class="form-control" id="body" placeholder="body">
              </div>

              <button class="btn btn-dark mt-2" @click="postEdit()" >Post Update</button>
            </form>
          </div>
          <b-button class="mt-3" @click="hideModal()" block>hide</b-button>
        </b-modal>
      </div>


      <form>
        <div class="row mt-5">
          <div class="col">
            <label for="title">Post id</label>
            <input type="number" v-model="form.userId" class="form-control" id="title" placeholder="id">
          </div>
          <div class="col">
            <label for="title">Post Title</label>
            <input type="text" v-model="form.title" class="form-control" id="title" placeholder="title">
          </div>
          <div class="col">
            <label for="body">Post Details</label>
            <input type="text" v-model="form.body" class="form-control" id="body" placeholder="body">
          </div>
        </div>
        <button @click="postSub()" class="btn btn-dark mt-2">Submit</button>
      </form>   


      <div class="row  mt-5">
        <div class="col-lg-3 mb-4" v-for="todo in todos" :key="todo.id">
          <div class="card px-2 py-2 text-center h-100">
            <h5 class="mt-5">{{todo.title}}</h5>
            <p class="mt-auto">{{todo.body}}</p>
            <a @click="hrfConcat(todo.id)" class="btn btn-sm card-btn mt-auto">Details</a>

            <b-button variant="success" size="sm" @click="showModal(todo.title,todo.body,todo.id)" class="mt-2" id="show-btn">Edit</b-button>
            <!-- <button @click="postEdit()" class="btn btn-sm btn-success mt-2">Edit</button> -->
            <button @click="postDelete(todo.id)" class="btn btn-sm btn-dark mt-2">Delete</button>



          </div>
        </div>

      </div>

    </div>



  </div>

</template>
<script>
export default {
  data(){
    return{
      todos:'',
      singlePost:'rwe',
      editForm:{
        title:'',
        Body:'',
        userId:''
      },
      
      form:{
        userId:'',
        title:'',
        body:'',

      }



    }
  },
  mounted() {
   this.getAllTodos(); 
 },
 methods: {
   async  getAllTodos() {

     this.todos =  await this.$axios.$get('https://jsonplaceholder.typicode.com/posts');
   },

   hrfConcat(todo_id){
    this.$router.push({ path: '/post_details', query: { todo_id: todo_id }})
    console.log (this.$router);
  },

  async  postSub(){
   event.preventDefault()
   const responce = await this.$axios.$post('https://jsonplaceholder.typicode.com/posts',this.form);
   this.getAllTodos()
   console.log(responce)


 },
 async postDelete(todo_id){
  await this.$axios.$delete('https://jsonplaceholder.typicode.com/posts/' + todo_id);
},
showModal(todo_title,todo_body,todo_id) {
  this.$refs['my-modal'].show();
  this.editForm.Body = todo_body;
  this.editForm.userId = todo_id;
  this.editForm.title = todo_title;


},
hideModal() {
  this.$refs['my-modal'].hide()
},


async postEdit(){
  event.preventDefault()
  const response = await this.$axios.$put('https://jsonplaceholder.typicode.com/posts/1',this.editForm);
  this.getAllTodos()
  console.log(response)

}


}
};
</script>

<style>
.card-btn{
  background-color: #FA7B58;
  padding-left: 30px;
  padding-right: 30px;
  font-weight: bold;
  color: white
}
.card{
  box-shadow: 0px 0px 5px 0px rgba(0,0,0,0.75);
}
.post-id{
  color: rgb(72,74,163);
  font-weight: bold;
  font-size: 40px;
  height: 60px;
  width: 60px;
  border-radius: 50%;
  margin-left: auto;
  margin-right: auto;
}



</style>
