<template>
  <button @click="onClick">Reset</button>
</template>

<script lang="ts">
import Vue from "vue";
import { createComponent, SetupContext } from "@vue/composition-api";

export default createComponent({
  props: {
    value: {
      type: String,
      default: null
    }
  },
  setup(props, context) {
    // created
    const initialValue = props.value
    
    
    const onClick = () => {
      context.emit("input", initialValue);
    };
    return {
      onClick
    };
  }
});
</script>
