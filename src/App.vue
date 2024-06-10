<script>
import PostLIst from "@/components/PostList.vue";
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyDialog from "@/components/UI/MyDialog.vue";
import MyButton from "@/components/UI/MyButton.vue";
import axios from "axios";
import MySelect from "@/components/UI/MySelect.vue";
export default {
  components:{
    MySelect,
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
      isPostLoading: false,
      selectedSort: '',
      sortOptions:[
        {value:'title',name:'По названию'},
        {value:'body',name:'По описанию'},
      ]
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
        this.isPostLoading = true
        const responce = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
        this.posts = responce.data

      }catch(e){
        alert('Ошибка')
      }finally{
        this.isPostLoading = false
      }

    },
  },
  mounted(){
    this.fetchPosts()
  }
}
</script>

<template>
  <div>
    <div class="app__btns">
      <my-button @click="showDialog">Создать</my-button>
      <my-select v-model="selectedSort" :options="sortOptions"></my-select>
    </div>

    <my-dialog v-model:show="dialogVisible" >
      <post-form @create="createPost"/>
    </my-dialog>
    <post-list v-if="!isPostLoading" :posts="posts" @remove="removePost"/>
    <div v-else>Идет загрузка...</div>
  </div>
</template>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app__btns{
  display: flex;
  justify-content: space-between;
}

</style>