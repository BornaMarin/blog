<template>
  <section class="posts-list">
    <PostPreview
      v-for="post in posts"
      :key="post.id"
      :id="post.id"
      :is-admin="isAdmin"
      :thumbnail="post.thumbnail"
      :title="post.title"
      :previewText="post.previewText "/>

  </section>
</template>
/*https://www.washingtonpost.com/resizer/C_c2_UabsQe7b0nvVhgf7gSprqk=/620x0/arc-anglerfish-washpost-prod-washpost.s3.amazonaws.com/public/NCPWU4FVKUI6RFHLHPKS37URPM.jpg*/
<script>
  import PostPreview from "./PostPreview";
  export default {
    components: {
      PostPreview
    },
    props: {
      isAdmin: {
        type: Boolean,
        default: false
      },
      posts: {
        type: Array,
        required: true

      }
    }
  }
</script>

<style scoped>
  .posts-list {
    display: flex;
    padding: 20px;
    box-sizing: border-box;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
  }


</style>
