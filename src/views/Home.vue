<template>
  <div class="home">
    <h1>Home</h1>
    <PostList :posts="posts" />
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import { ref } from 'vue'

export default {
  name: 'Home',
  components: { PostList },
  setup(){
    const posts = ref ([
      { title:'welcome in the blog', body:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloremque animi explicabo atque sed, perspiciatis, expedita deserunt impedit corrupti dicta, cum aliquid natus architecto temporibus? Cum beatae totam corrupti id eius.', id: 1 },
      { title:'top 5 css tips', body:'lorem ipsum', id: 2 },
    ])
    return { posts }
  }
}
</script>

