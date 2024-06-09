<script>
import PostLIst from "@/components/PostList.vue";
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
export default {
  components:{
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
    }
  },
  methods:{
    createPost(post){
      this.posts.push(post)
    }
  }
}
</script>

<template>
  <div>
    <post-form @create="createPost"/>
    <post-list :posts="posts" />
  </div>
</template>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

</style>