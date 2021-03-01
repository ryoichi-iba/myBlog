<template>
  <main>
    <h1>{{ title }}</h1>
    <p>{{ date }}</p>
    <div v-html="contents"></div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
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