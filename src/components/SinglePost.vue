<template>
  <li>
    <div style="display: inline-block; padding-right: 10px;" :class="{ 'fav': post.fav }">{{ post.title }}</div> |
    <button @click="handleClick(post)">Delete Post</button> |
    <button v-if="post.fav == false" @click="$emit('fav', post)">Like</button>
    <button v-if="post.fav == true" @click="$emit('fav', post)">unLike</button>
  </li>
</template>

<script>
export default {
  name: "SinglePost",
  props: ['post'],
  methods: {
    handleClick(post) {
      this.$emit('delete', post)
    }
  }
}
</script>

<style scoped>
.fav {
  color: green;
}
</style>