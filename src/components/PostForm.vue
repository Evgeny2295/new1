<script>
export default {
  data(){
    return {
      post:{
        title:'',
        body:''
      }
    }
  }
}
</script>

<template>
  <form action="" @submit.prevent>
    <input @input="post.title=$event.target.value" v-bind:value="post.title" type="text" class="input" placeholder="Введите название">
    <input @input="post.body=$event.target.value" v-bind:value="post.body" type="text" class="input" placeholder="Введите описание">
    <button @click="createPost" class="btn">Добавить</button>
  </form>
</template>

<style scoped>

</style>