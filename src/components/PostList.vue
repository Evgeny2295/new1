<script setup>
export default {
  props:{
    posts:{
      type:Array,
      required:true
    }
  }
}

</script>

<template>
  <div>
    <div class="post" v-for="post in posts">
      <div><strong>Название:</strong>{{ post.title }}</div>
      <div><strong>Описание:</strong>{{ post.body }}</div>
    </div>
  </div>

</template>

<style scoped>


.post{
  padding: 15px;
  border: 2px solid blue;
  margin-top: 15px;
}
</style>