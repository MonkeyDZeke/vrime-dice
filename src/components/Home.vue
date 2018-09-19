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
// h3 {
//   margin: 40px 0 0;
// }
// ul {
//   list-style-type: none;
//   padding: 0;
// }
// li {
//   display: inline-block;
//   margin: 0 10px;
// }
// a {
//   color: #42b983;
// }
</style>
