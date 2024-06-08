<script>
export default {
  data(){
    return{
      likes:0,
      disLikes:0
    }
  },
  methods:{
    addLikes(){
      this.likes +=1;
    },
    addDisLikes(){
      this.disLikes +=1;
    }
  }
}
</script>

<template>
  <div>
    <div>Количество лайков: {{likes}}</div>
    <div>Количество дизлайков: {{disLikes}}</div>
    <button v-on:click="addLikes">Нравится</button>
    <button v-on:click="addDisLikes">не нравится</button>
  </div>
</template>

<style scoped>

</style>