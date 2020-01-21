<template>
  <button @click="onClick">My Button</button>
</template>

<script lang="ts">
import { Component, Vue, Prop, Emit } from "vue-property-decorator";

@Component
export default class MyButton extends Vue {
  private count: number = 0;
  @Prop()
  public great?: string;

  @Emit()
  public click(count: number) {
  }
  public onClick() {
      alert(this.great);
      this.count++;
      this.click(this.count)
    }
};
</script>
