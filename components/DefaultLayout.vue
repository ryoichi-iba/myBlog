<template>
  <div class="app-container">
    <header>
      <div class="site-title">
        <nuxt-link to="/" class="site-title__link">suzukazuブログ</nuxt-link>
      </div>
    </header>
     <slot/>
  </div>
</template>
<script>
export default {
  
}
</script>
<style lang="scss" scoped>
.app-container {
  max-width: 720px;
  margin-right: auto;
  margin-left: auto;
  padding: 20px;
}
.site-title {
  font-size: 46px;
  line-height: 1.3;
  font-weight: bold;
  text-align: center;
  &__link {
    color: black;
    opacity: 1;
    text-decoration: none;
  }
}
.site-description {
  margin-top: 6px;
  text-align: center;
}
.main {
  margin-top: 30px;
}
</style>