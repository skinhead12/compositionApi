<template>
    <div class="details">
      <h1>Detail</h1>
      <div v-if="error" >{{ error }}</div>
      <div v-if="post" class="post">
        <h3>{{ post.title }}</h3>
        <p class="pre">{{ post.body }}</p>
    </div>
    </div>
  </template>
  
  <script>
    import getOtherPost from '@/composables/getOtherPost';

  export default {
    name: 'Detail',
    props: ['id'],
    setup(props){
        const { post, error, load } = getOtherPost(props.id)

        load()

        return { post, error, load }
    }
  }
  </script>

  <style>
  .post {
    max-width: 1200px;
    margin: 0 auto;
  }
  .post p {
    color: #444;
    line-height: 1.5em;
    margin-top: 40px;
  }
  .pre {
    white-space: pre-wrap;
  }
</style>