<template>
  <button @click="onClick">Reset</button>
</template>

<script lang="ts">
import { Component, Vue, Prop, Emit } from "vue-property-decorator";

@Component
export default class ResetButton extends Vue {
  private initialValue!: string;
  @Prop()
  value!: string;

  /** ライフサイクルフック */
  public created() {
    this.initialValue = this.value;
  }

  @Emit()
  public input(value: string) {
  }
  public onClick() {
    this.input(this.initialValue);
  }
}
</script>
