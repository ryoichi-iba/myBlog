<template>
  <main>
    <h2 class="post_title">{{ title }}</h2>
    <p class="post_date">Posted at  {{ dateFormat(date) }}</p>
    <hr>
    <div v-html="contents" class="post_content"></div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  methods: {
      dateFormat(dateString) {
          return this.$dateformat(new Date(dateString), 'yyyy-mm-dd');
      }
    },
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://suzukazu-blog.microcms.io/api/v1/blog/${params.slug}`,
      {
        headers: { "X-API-KEY": process.env.MICRO_CMS_API }
      }
    )
    return data
  }
}
</script>

<style lang="scss">
  .post_title {
    font-size: 27px;
    font-weight: bold;
    margin-top: 25px;
  }

  .post_date {
    margin: 5px 0;
  }

  .post_content {
    margin: 20px 0;
    font-size: 1.05rem;
  }
</style>