<template>
  <main>
    <div class="" v-for="content in contents" :key="content.id">
      <nuxt-link :to="`/blog/${content.id}`" class="post">
        <h1 class="post-head">
          <div class="post-head__title">
            {{ content.title }}
          </div>
        </h1>
      </nuxt-link>
        <p class="post-date">
          {{ content.date }}
        </p>
    </div>
  </main>
</template>
<script>
  import axios from "axios";
  export default {
    async asyncData() {
      const {
        data
      } = await axios.get(
        // 5-2でメモしたURLを記載しましょう。
        "https://suzukazu-blog.microcms.io/api/v1/blog", {
          // 5-2でメモしたAPIキーを記載しましょう。
          headers: {
            "X-API-KEY": process.env.MICRO_CMS_API
          }
        }
      );
      return data;
    }
  };

</script>
<style lang="scss" scoped>


  a {
    color: black;
    &:hover {
      opacity: 0.7;
      text-decoration: none;
    }
  }

  .post {
    color: black;
    &:hover {
      opacity: 0.7;
      text-decoration: none;
    }
  }

  .post-head {
    font-size: 1.5rem;
    margin-top: 20px;
    margin-bottom: 4px;
    font-weight: bold;

      &:hover {
          opacity: 0.7;
          text-decoration: none;
        }
    &__title {
      color: black;
    }
  }

  // .post-date {
  //    &:hover {
  //         opacity: 0.7;
  //         text-decoration: none;
  //       }
  // }

</style>
