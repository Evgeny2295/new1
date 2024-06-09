<script>
export default {
  data(){
    return {
      post:{
        title:'',
        body:''
      }
    }
  },
  methods:{
    createPost(){

      this.post.id = Date.now();
      this.$emit('create',this.post);
      this.post = {
        title:'',
        body:''
      }
    }
  }
}
</script>

<template>
  <form action="" @submit.prevent>
    <input v-model="post.title" type="text" class="input" placeholder="Введите название">
    <input v-model="post.body" type="text" class="input" placeholder="Введите описание">
    <button @click="createPost" class="btn">Добавить</button>
  </form>
</template>

<style scoped>

</style>