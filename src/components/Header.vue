<template>
  <div class="header">
    <h1>{{ gameName }}</h1>
    <h2>Welcome to my {{ gameName }} Game</h2>
    <p>
      Use the alphabet below to guess the word. You have {{ lives }} lives so
      try your best.
    </p>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "Header",
  setup() {
    const lives = ref(10);
    const gameName = ref("Hangman");

    return {
      lives: lives,
      gameName: gameName,
    };
  },
};
</script>
