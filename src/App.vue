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
      title:'',
      body:''
    }
  },
  methods:{
    createPost(){
      const newPost = {
        id: Date.now(),
        title:this.title,
        body:this.body
      }
      this.posts.push(newPost);
      this.title = '';
      this.body = '';
    }
  }
}
</script>

<template>
  <div>
    <post-form/>
    <post-list :posts="posts"/>
  </div>
</template>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

</style>