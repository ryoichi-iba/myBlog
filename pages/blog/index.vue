<template>
  <main>
    <h1>ブログ一覧</h1>
    <ul>
      <li v-for="content in contents" :key="content.id">
        <nuxt-link :to="`/blog/${content.id}`">
          {{ content.title }}
        </nuxt-link>
      </li>
    </ul>
  </main>
</template>
<script>
import axios from "axios";
export default {
  mounted() {
    console.log(process.env.MICRO_CMS_API);
  },

  async asyncData() {
    const { data } = await axios.get(
      // 5-2でメモしたURLを記載しましょう。
      "https://suzukazu-blog.microcms.io/api/v1/blog",
      {
        // 5-2でメモしたAPIキーを記載しましょう。
        headers: { "X-API-KEY": process.env.MICRO_CMS_API }
      }
    );
    return data;
  }
};
</script>
<style></style>
