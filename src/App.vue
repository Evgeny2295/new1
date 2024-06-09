<script>
export default {
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
    <form action="" @submit.prevent>
      <input @input="title=$event.target.value" v-bind:value="title" type="text" class="input" placeholder="Введите название">
      <input @input="body=$event.target.value" v-bind:value="body" type="text" class="input" placeholder="Введите описание">
      <button @click="createPost" class="btn">Добавить</button>
    </form>
    <div class="post" v-for="post in posts">
      <div><strong>Название:</strong>{{ post.title }}</div>
      <div><strong>Описание:</strong>{{ post.body }}</div>
    </div>
  </div>
</template>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.post{
  padding: 15px;
  border: 2px solid blue;
  margin-top: 15px;
}
</style>