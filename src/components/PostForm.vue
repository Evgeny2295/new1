<script>
import MyInput from "@/components/UI/MyInput.vue";

export default {
  components: {MyInput},
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
    <my-input v-model:value="post.title" placeholder="Введите название"/>
    <my-input v-model="post.body" placeholder="Введите описание"/>
    <my-button @click="createPost" class="btn">Создать</my-button>
  </form>
</template>

<style scoped>

</style>