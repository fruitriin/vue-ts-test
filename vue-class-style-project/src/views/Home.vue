<template>
  <div class="home">
    <p>{{ greatText }}</p>
    <p>挨拶した回数 : {{ count }}回</p>
    <p v-if="isRegulars">いつもありがとうございます</p>
    <p>
      <MyButton :great="greatText" @click="onMyButtonClicked" />
    </p>
    <p>
      <ResetButton initialValue="Hello" v-model="greatText" />
    </p>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from "vue-property-decorator";
// @ is an alias to /src
import MyButton from "@/components/MyButton.vue";
import ResetButton from "@/components/ResetButton.vue";

@Component({
  components: {
    MyButton,
    ResetButton
  }
})
export default class Home extends Vue {
  public greatText: string = "Hello";
  private count: number = 0;

  public onMyButtonClicked(count: number) {
    this.greatText = "こんにちわ";
    this.count = count;
  }
  public get isRegulars(): boolean {
    return this.count >= 3;
  }
  @Watch("count")
  public countChange() {
    if (this.count === 3) {
      alert("常連になりました");
    }
  }
}
</script>
