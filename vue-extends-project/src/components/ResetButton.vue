<template>
  <button @click="onClick">Reset</button>
</template>

<script lang="ts">
import Vue from "vue";

export type DataType = {
  initialValue: string | null;
};
export default Vue.extend({
  data(): DataType {
    return {
      initialValue: null
    };
  },
  props: {
    value: {
      type: String,
      default: null
    }
  },
  created() {
    this.initialValue = this.value;
  },
  methods: {
    input(value: string| null) {
      this.$emit("input", value);
    },
    onClick() {
      this.input(this.initialValue);
    }
  }
});
</script>
