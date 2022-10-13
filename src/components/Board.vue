<template>
  <div class="board">
    <div class="buttons">
      <div class="alphabet">
        <Button
          @showLetter="guessLetter"
          :key="letter.index"
          v-for="letter in alphabet"
          :letter="letter"
        />
      </div>
    </div>

    <br />
    <div class="solution">
      <Button
        :key="solutionLetter.index"
        v-for="solutionLetter in solution"
        :letter="solutionLetter.letter"
        :hide-content="!solutionLetter.guessed"
      />
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import Button from "./Button";

export default {
  name: "Board",
  components: {
    Button,
  },

  setup() {
    const solution = ref([]);
    const words = ref([
      "tree",
      "party",
      "layout",
      "image",
      "seal",
      "berlin",
      "project",
      "structure",
    ]);
    const alphabet = ref([..."abcdefghijklmnopqrstuvwxyz"]);

    const newGame = () => {
      solution.value = [];
      const randomWord = randomWords();
      for (let i in randomWord) {
        solution.value.push({ letter: randomWord[i], guessed: false });
      }
    };

    const randomWords = () => {
      return words.value.sort(() => Math.random() - 0.5)[0];
    };

    const guessLetter = (letter) => {
      console.log("guessLetter");
      for (let solutionLetter of solution.value) {
        if (letter === solutionLetter.letter) {
          solutionLetter.guessed = true;
          console.log("set true");
        }
      }
    };

    newGame();

    return {
      alphabet,
      solution,
      newGame,
      guessLetter,
    };
  },
};
</script>
