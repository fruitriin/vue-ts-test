<template>
  <button @click="onClick">My Button</button>
</template>

<script lang="ts">
import Vue from "vue";

export type DataType = {
  count: number;
};

export default Vue.extend({
  data(): DataType {
    return {
      count: 0
    };
  },
  props: {
    great: {
      type: String,
      default: null
    }
  },
  methods: {
    onClick() {
      alert(this.great);
      this.count++;
      this.$emit("click", this.count);
    }
  }
});
</script>
