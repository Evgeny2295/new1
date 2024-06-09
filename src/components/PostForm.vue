<script setup>

</script>

<template>
  <form action="" @submit.prevent>
    <input @input="title=$event.target.value" v-bind:value="title" type="text" class="input" placeholder="Введите название">
    <input @input="body=$event.target.value" v-bind:value="body" type="text" class="input" placeholder="Введите описание">
    <button @click="createPost" class="btn">Добавить</button>
  </form>
</template>

<style scoped>

</style>