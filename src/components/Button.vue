<template>
  <div @click="showLetter" class="letter">
    <span :style="spanStyles">{{ letter }}</span>
  </div>
</template>

<script>
import { computed } from "vue";

export default {
  name: "Button",
  props: {
    letter: String,
    hideContent: {
      type: Boolean,
      default: false,
    },
  },

  setup(props, context) {
    const spanStyles = computed(function () {
      const display = props.hideContent ? "none" : "block";
      return `display: ${display}`;
    });

    const showLetter = () => {
      console.log("showLetter");
      context.emit("show-letter", props.letter);
    };

    return {
      spanStyles,
      showLetter,
    };
  },
};
</script>
