<template>
  <div id="app" class="section">
    <div class="columns">
      <div class="column is-three-fifths is-offset-one-fifth">
        <figure class="image is-square">
          <img alt="Grime Diagram" src="./assets/grimeonediediagram.png">
        </figure>
        <Home msg="Welcome to Vrime Dice!"/>
      </div>
    </div>
    <div class="columns">
      <div class="column is-three-fifths is-offset-one-fifth">
        <div class="buttons is-centered">
          <a @click.prevent="pools += 1" class="button is-large is-rounded is-primary">
            Add a New Pool
          </a>
        </div>
        <Game v-bind:pools="pools" />
      </div>
    </div>
  </div>
</template>

<script>
import Home from './components/Home.vue';
import Game from './components/Game.vue';

export default {
  name: 'app',
  data() {
    return {
      pools: 1,
    };
  },
  components: {
    Home,
    Game,
  },
};
</script>

<style lang="scss">

@charset "utf-8";

// Import a Google Font
@import url('https://fonts.googleapis.com/css?family=Fjalla+One');

// Set your brand colors
$green: #365e35;
$black-bis: #111111;
$turquoise: #b7f0e7;
$brown: #757763;
$beige-light: #D0D1CD;
$beige-lighter: #EFF0EB;

// Update Bulma's global variables
$family-sans-serif: "Fjalla One", sans-serif;
$grey-dark: $brown;
$grey-light: $beige-light;
$dark: $black-bis;
$primary: $green;
$link: $turquoise;
$widescreen-enabled: false;
$fullhd-enabled: false;

// Update some of Bulma's component variables
$body-background-color: $beige-lighter;

// Import only what you need from Bulma
@import "../node_modules/bulma";

</style>
