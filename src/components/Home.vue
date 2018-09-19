<template>
  <div class="hello notification is-primary has-text-dark">
    <h1 class="title">{{ msg }}</h1>
    <p>
      For the math and science behind this project, check out the
      <a href="http://singingbanana.com/dice/article.htm" target="_blank" class="has-text-link" rel="noopener">original paper</a>.
    </p>
  </div>
</template>

<script>
export default {
  name: 'Home',
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
