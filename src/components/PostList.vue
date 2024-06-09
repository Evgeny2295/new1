<script>
import PostItem from "@/components/PostItem.vue";

export default {
  components: {PostItem},
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
    <div v-if="posts.length > 0">
      <h3>Список пользователей</h3>
      <post-item
          v-for="post in posts"
          :post="post"
          :key="post.id"
          @remove="$emit('remove',post)"
      />
    </div>
    <div v-else>
      <h3>Список пользователей пуст</h3>
    </div>

  </div>

</template>

<style scoped>



</style>