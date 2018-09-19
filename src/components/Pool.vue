<template>
  <div class="box">
    <div class="buttons has-addons">
      <a
        v-show="setup"
        v-for="(die, id) in dice"
        :key="id"
        @click.prevent="addDie(id, 'set1')"
        :class="'button ' + id">
        {{ die.name }}
      </a>
    </div>
    <div class="buttons has-addons">
      <a
        v-show="setup"
        v-for="(die, id) in dice"
        :key="id"
        @click.prevent="addDie(id, 'set2')"
        :class="'button ' + id">
        {{ die.name }}
      </a>
    </div>
    <div class="message">
      <div class="message-header">Set One</div>
      <div class="message-body">
        <span
          v-for="(die, index) in set1"
          :key="index * Date.now()"
          :class="'tag is-rounded ' + dice[die].name">
          {{ dice[die].name }}
          <button @click.prevent="set1.splice(index, 1)" class="delete is-small"></button>
        </span>
      </div>
    </div>
    <div class="message">
      <div class="message-header">Set One</div>
      <div class="message-body">
        <span
          v-for="(die, index) in set2"
          :key="index * Date.now()"
          :class="'tag is-rounded ' + dice[die].name">
          {{ dice[die].name }}
          <button @click.prevent="set2.splice(index, 1)" class="delete is-small"></button>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'pool',
  methods: {
    addDie(id, set) {
      this[set].push(this.dice[id].name);
    },
  },
  data() {
    return {
      setup: true,
      set1: [],
      set2: [],
      dice: {
        Blue: {
          name: 'Blue',
          sides: [2, 2, 2, 7, 7, 7],
        },
        Magenta: {
          name: 'Magenta',
          sides: [1, 1, 6, 6, 6, 6],
        },
        Olive: {
          name: 'Olive',
          sides: [0, 5, 5, 5, 5, 5],
        },
        Red: {
          name: 'Red',
          sides: [4, 4, 4, 4, 4, 9],
        },
        Yellow: {
          name: 'Yellow',
          sides: [3, 3, 3, 3, 8, 8],
        },
      },
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.Blue {
  background-color: #95caff;
}
.Magenta {
  background-color: #ea95ff;
}
.Olive {
  background-color: #c5ff95;
}
.Red {
  background-color: #ff9595;
}
.Yellow {
  background-color: #fff495;
}

</style>
