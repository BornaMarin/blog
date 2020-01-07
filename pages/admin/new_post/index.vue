<template>
  <div class="admin-new-post-page">
    <section class="new-post-form">
      <adminPostForm @submit="onSubmitted" />
    </section>
  </div>
</template>

<script>
  import axios from 'axios'
  import adminPostForm from "../../../components/Admin/adminPostForm";
  export default {
    layout: 'admin',
    components: {
      adminPostForm
    },
    methods: {
      onSubmitted(postData){
          axios.post('https://nuxtblog-bb445.firebaseio.com/posts.json', {
            ...postData, updatedDate: new Date()})
          .then(result => console.log(result))
          .catch(e => console.log(e))
      }
    }
  }
</script>

<style scoped>
  .new-post-form {
    width: 90%;
    margin: 20px auto;
  }

  @media (min-width: 768px) {
    .new-post-form {
      width: 500px;
    }
  }
</style>
