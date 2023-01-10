<script>
import SinglePost from "../components/SinglePost.vue";

export default {
  name: "HomePage",
  components: { SinglePost },
  data() {
    return {
      message: "Hello Bangladesh",
      posts: [
        {
          id: 1,
          title: "Post 1",
          fav: true
        },
        {
          id: 2,
          title: "Post 2",
          fav: false
        },
        {
          id: 3,
          title: "Post 3",
          fav: true
        }
      ],
    }
  },
  computed: {
    favs() {
      return this.posts.filter(post => post.fav)
    },
    unFavs() {
      return this.posts.filter(post => !post.fav)
    },
    favCount() {
      return this.posts.filter(post => post.fav).length
    },
    unFavCount() {
      return this.posts.filter(post => !post.fav).length
    },
    postCount() {
      return this.posts.filter(post => post).length
    }
  },
  methods: {
    handleDelete(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    addPost() {
      this.posts.push({
        id: this.posts.length + 1,
        title: `Post ${this.posts.length + 1}`,
        fav: true
      })
    },
    handleFav(post) {
      this.posts = this.posts.map(p => {
        if (p.id === post.id) {
          p.fav = !p.fav
        }
        return p
      })
    }
  }

}
</script>

<template>
  <button @click="addPost">Add Post</button>
  <br>

  <h1 class="posts">Posts {{ postCount }}</h1>
  <ul>
    <single-post style="margin-bottom: 10px" v-for="(post, index) in posts" :key="index" :post="post"
      @delete="handleDelete" @fav="handleFav" />
  </ul>
  <br>
  <h1 class="liked">Liked - {{ favCount }}</h1>
  <ul>
    <single-post style="margin-bottom: 10px" v-for="(post, index) in favs" :key="index" :post="post"
      @delete="handleDelete" @fav="handleFav" />
  </ul>
  <br>
  <h1 class="diliked">Disliked - {{ unFavCount }}</h1>
  <ul>
    <single-post style="margin-bottom: 10px" v-for="(post, index) in unFavs" :key="index" :post="post"
      @delete="handleDelete" @fav="handleFav" />
  </ul>
</template>

<style scoped>
.diliked {
  color: red;
}

.liked {
  color: rgb(38, 95, 46);
}

.posts {
  color: rgb(7, 121, 187);
}
</style>