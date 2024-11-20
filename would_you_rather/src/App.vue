<script setup>
import WouldYouRather from "./components/WouldYouRather.vue";

import { ref } from "vue";

const wyrQuestion = ref("Live in a triangle or a circle?");
const wyrAnswer1 = ref("Triangle");
const wyrAnswer2 = ref("Circle");

// This will store the user's answer after making a choice

const userSelection = ref("");

function updateUserSelection(userChoice) {
  userSelection.value = `Thanks! you chose ${userChoice}`;
  // updates whatever is in const userSelection with whatever the user chose (userChoice)

  // choice.value in WouldYouRather.vue will be included in the answer selected event when it is emited.
  // When the event happens (when WouldYouRather shown below recieves an answer-selected event, it will call updateUserSelection) and whatever is in choice.value in WouldYouRather.vue will end up in the above function in userChoice in order to utalize it in App.vue.
  // in this case we use it to set it to userSelection.value.
}
</script>

<template>
  <div id="app-component">
    <h1>Would You Rather?</h1>

    <WouldYouRather
      v-bind:question="wyrQuestion"
      v-bind:answer1="wyrAnswer1"
      v-bind:answer2="wyrAnswer2"
      v-on:answer-selected="updateUserSelection"
    >
    </WouldYouRather>
    <!-- Here we use bind to connect "question" from WouldYouRather file to the wyrQuestion const defined in the App.vue files script. It sends all of the data to the props in WouldYouRather.vue -->
    <p>{{ userSelection }}</p>
  </div>
</template>
<!-- Vue specific component-->

<style scoped>
p {
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
}
#app-component {
  background-color: darkolivegreen;
}
</style>
