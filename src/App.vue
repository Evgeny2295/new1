<script>
import PostLIst from "@/components/PostList.vue";
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyDialog from "@/components/UI/MyDialog.vue";
import MyButton from "@/components/UI/MyButton.vue";
import axios from "axios";
export default {
  components:{
    MyButton,
    MyDialog,
    PostList,
    PostForm,PostLIst
  },

  data(){
    return{
     posts: [

     ],
      dialogVisible:false,
    }
  },
  methods:{
    createPost(post){
      this.posts.push(post)
      this.dialogVisible = false
    },
    removePost(post){
      this.posts = this.posts.filter(p=>p.id !== post.id)
    },
    showDialog(){
      this.dialogVisible = true
    },
    async fetchPosts(){
      try{
        const responce = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
        this.posts = responce.data
      }catch(e){
        alert('Ошибка')
      }
    }
  }
}
</script>

<template>
  <div>
    <my-button @click="fetchPosts">Получить посты</my-button>
    <my-button @click="showDialog">Создать</my-button>
    <my-dialog v-model:show="dialogVisible" >
      <post-form @create="createPost"/>
    </my-dialog>
    <post-list :posts="posts" @remove="removePost" />
  </div>
</template>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

</style>