<template>
  <div class="columns">
    <div class="column">
      <div
        v-for="roll in rolls.results1"
        :key="roll.i"
        class="box">
        <ul>
          <li v-for="(die, j) in roll.dice" :key="j">{{die}}</li>
        </ul>
      </div>
    </div>
    <div class="column">
      <div
        v-for="roll in rolls.results2"
        :key="roll.i"
        class="box">
        <ul>
          <li v-for="(die, j) in roll.dice" :key="j">{{die}}</li>
        </ul>
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
