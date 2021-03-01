<template>
  <div>
    <h1>{{ title }}</h1>
  </div>
</template>
<script>
export default {
  data() {
    return {
      title: "アバウトページ"
    };
  },
  head() {
    return {
      title: this.title,
      meta: [
        { hid: "description", name: "description", content: "description" }
      ]
    };
  }
};
</script>
<style lang="scss"></style>