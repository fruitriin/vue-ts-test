<template>
  <button @click="onClick">My Button</button>
</template>

<script>
export default {
  data() {
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
};
</script>
