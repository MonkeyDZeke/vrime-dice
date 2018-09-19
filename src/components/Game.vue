<template>
  <div class="column">
    <Pool v-for="n in pools" :key="n" />
  </div>
</template>

<script>
import Pool from './Pool.vue';

export default {
  name: 'game',
  props: {
    pools: Number,
  },
  components: {
    Pool,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
