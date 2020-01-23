<template>
  <button @click="onClick">My Button</button>
</template>

<script lang="ts">
import Vue from "vue";
import { createComponent } from "@vue/composition-api";

export default createComponent({
  props: {
    great: {
      type: String,
      default: null
    }
  },

  setup(props, context) {
    let count = 0;
    const onClick = () => {
      alert(props.great);
      count++;
      context.emit("click", count);
    };

    return {
      onClick
    };
  }
});
</script>
