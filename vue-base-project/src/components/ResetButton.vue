<template>
  <button @click="onClick">Reset</button>
</template>

<script>
export default {
  data() {
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
    input(value) {
      this.$emit("input", value);
    },
    onClick() {
      this.input(this.initialValue);
    }
  }
};
</script>
