<template>
  <div class="box">
    <div class="level">
      <a
        v-show="set1.length && set2.length"
        class="button is-fullwidth is-rounded"
        @click.prevent="rollDice">
        Roll Dice!
      </a>
    </div>
    <div class="message is-dark">
      <div class="message-header">
        <p :class="this.winner > 0 ? 'has-text-success' : this.winner < 0 ? 'has-text-danger' : ''">
          Set One
          <span
            v-for="(fight, i) in wins"
            :key="i"
            class="icon"
            :class="fight[0] ? 'has-text-success' : 'has-text-danger'">
            <sword-cross class="mdi" :class="fight[0] ? 'mdi-flip-v' : ''"/>
          </span>
        </p>
        <div class="buttons has-addons">
          <a
            :title="die.sides.join(', ')"
            v-show="setup"
            v-for="(die, id) in dice"
            :key="id"
            @click.prevent="addDie(id, 'set1')"
            :class="'button ' + id">
            {{ die.name }}
          </a>
        </div>
      </div>
      <div class="message-body">
        <span
          v-for="(die, index) in set1"
          :key="index * Date.now()"
          :title="dice[die].sides.join(', ')"
          :class="'tag is-rounded ' + dice[die].name">
          {{ dice[die].name }}
          <button
            @click.prevent="set1.splice(index, 1)"
            v-show="setup"
            class="delete is-small"></button>
        </span>
      </div>
    </div>
    <div class="message is-dark">
      <div class="message-header">
        <p :class="this.winner < 0 ? 'has-text-success' : this.winner > 0 ? 'has-text-danger' : ''">
          Set Two
          <span
            v-for="(fight, i) in wins"
            :key="i"
            class="icon"
            :class="fight[1] ? 'has-text-success' : 'has-text-danger'">
            <sword-cross />
          </span>
        </p>
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
      </div>
      <div class="message-body">
        <span
          v-for="(die, index) in set2"
          :key="index * Date.now()"
          :title="dice[die].sides.join(', ')"
          :class="'tag is-rounded ' + dice[die].name">
          {{ dice[die].name }}
          <button
            @click.prevent="set2.splice(index, 1)"
            v-show="setup"
            class="delete is-small"></button>
        </span>
      </div>
    </div>
    <Rolls v-show="rolls.length" v-bind:rolls="rolls" />
  </div>
</template>

<script>
import SwordCross from 'vue-material-design-icons/SwordCross.vue';
import Rolls from './Rolls.vue';

function arand(a) {
  return a[Math.floor(Math.random() * a.length)];
}

export default {
  name: 'pool',
  methods: {
    addDie(id, set) {
      this[set].push(this.dice[id].name);
    },
    rollDice() {
      const results1 = this.set1.map(die => arand(this.dice[die].sides));
      const results2 = this.set2.map(die => arand(this.dice[die].sides));
      const sum1 = results1.reduce((a, b) => a + b, 0);
      const sum2 = results2.reduce((a, b) => a + b, 0);
      this.rolls.push({
        results1,
        results2,
        sum1,
        sum2,
        i: this.rolls.length + 1,
      });
    },
  },
  data() {
    return {
      set1: [],
      set2: [],
      rolls: [],
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
  computed: {
    winner() {
      return this.rolls
        .reduce((a, r) => (r.sum1 > r.sum2 ? a + 1 : a - 1), 0);
    },
    wins() {
      return this.rolls.map(r => [r.sum1 > r.sum2, r.sum2 > r.sum1]);
    },
    setup() {
      return this.rolls.length === 0;
    },
  },
  components: {
    Rolls,
    SwordCross,
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
