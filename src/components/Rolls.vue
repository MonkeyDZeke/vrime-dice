<template>
  <div class="field is-grouped is-grouped-multiline">
    <div
      class="control"
      v-for="roll in rolls"
      :key="roll.i">
      <div class="tags has-addons">
        <span class="tag" :class="roll.sum1 > roll.sum2 ? 'is-success' : 'is-danger'">
          <strong class="has-text-white">
            Set One:&nbsp;
          </strong>
          {{ roll.results1.join(', ') }} = {{ roll.sum1 }}
        </span>
        <span class="tag" :class="roll.sum2 > roll.sum1 ? 'is-success' : 'is-danger'">
          <strong class="has-text-white">
            Set Two:&nbsp;
          </strong>
          {{ roll.results2.join(', ') }} = {{ roll.sum2 }}
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'rolls',
  props: ['rolls'],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
