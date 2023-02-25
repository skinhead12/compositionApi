<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error"> {{ error }}</div>
    <div v-if="posts.length"> 
      <PostList v-if="showPosts" :posts="posts" />
    </div>
    <div v-else>Loading...</div>
    <button @click="showPosts = !showPosts">toggle posts</button>
    <button @click="posts.pop()">delete a post</button>
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import { ref } from 'vue'

export default {
  name: 'Home',
  components: { PostList },
  setup(){
   /*  const posts = ref ([
      { title:'welcome in the blog', body:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Doloremque animi explicabo atque sed, perspiciatis, expedita deserunt impedit corrupti dicta, cum aliquid natus architecto temporibus? Cum beatae totam corrupti id eius.', id: 1 },
      { title:'top 5 css tips', body:'lorem ipsum', id: 2 },
    ]) */
    const posts = ref ([])
    const error = ref(null)

    const load = async () => {
      try {
        let data = await fetch('http://localhost:3000/posts')
        if (!data.ok){
          throw Error('no data available')
        }
        posts.value = await data.json()
      }
      catch (err){
        error.value = err.message
        console.log(err.value);
      }
    }
    load()
    
    return { posts, error }
  }
}
</script>

