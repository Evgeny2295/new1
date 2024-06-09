<script>
import PostLIst from "@/components/PostList.vue";
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyDialog from "@/components/UI/MyDialog.vue";
import MyButton from "@/components/UI/MyButton.vue";
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
       {id:1, title: 'javaScript', body: 'описание о Javascript'},
       {id:2, title: 'javaScript 2', body: 'описание о Javascript 2'},
       {id:3, title: 'javaScript 3', body: 'описание о Javascript 3'},
     ],
      dialogVisible:false,
    }
  },
  methods:{
    createPost(post){
      this.posts.push(post)
    },
    removePost(post){
      this.posts = this.posts.filter(p=>p.id !== post.id)
    },
    showDialog(){
      this.dialogVisible = true
    }
  }
}
</script>

<template>
  <div>
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