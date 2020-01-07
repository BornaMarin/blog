<template>
  <div class="admin-post-page">
    <section class="update-form">
        <adminPostForm  :post="loadedPost" @sumbit="OnSubmitted"/>


    </section>
  </div>
</template>
<script>
  import axios from 'axios';
  import adminPostForm from "../../../components/Admin/adminPostForm";
  export default {
    components: {
      adminPostForm
    },
    layout: 'admin',
    asyncData(context){
      return axios.get('https://nuxtblog-bb445.firebaseio.com/posts/'+ context.params.postId + '.json')
      .then(res => {
        return  {
          loadedPost: res.data
        }
      }).catch(e => context.error(e))
    },
    methods: {
      OnSubmitted(editedPost){
        axios.put('https://nuxtblog-bb445.firebaseio.com/posts/'+ this.$route.params.id + '.json')
        .then(res =>console.log(res))
        .catch(e => console.log(e))
      }
    }

  }
</script>
<style scoped>
  .update-form {
    width: 90%;
    margin: 20px auto;
  }
  @media (min-width: 768px) {
    .update-form {
      width: 500px;
    }
  }
</style>
