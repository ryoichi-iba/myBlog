<template>
  <main>
    <h1>ブログ一覧</h1>

    <div class="container">
      <div class="row justify-content-center">
          <div class="col-4 pt-5"  v-for="content in contents" :key="content.id">

            <b-card img-src="https://picsum.photos/600/300/?image=25" img-alt="Image" img-top tag="article"
              class="mb-2">
              <nuxt-link :to="`/blog/${content.id}`">
                {{ content.title }}
              </nuxt-link>
            </b-card>
          </div>
        </div>


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
<style></style>
