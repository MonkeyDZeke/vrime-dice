<template>
  <div v-show="setup" class="box">Setup</div>
</template>

<script>
export default {
  name: 'pool',
  data() {
    return {
      setup: true,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
