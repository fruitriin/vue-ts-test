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
import Vue from "vue";
// @ is an alias to /src
import MyButton from "@/components/MyButton.vue";
import ResetButton from "@/components/ResetButton.vue";

export type DataType = {
  greatText: string;
  count: number;
};

export default Vue.extend({
  data(): DataType {
    return {
      greatText: "Hello",
      count: 0
    };
  },
  
  components: {
    MyButton,
    ResetButton
  },

  methods: {
    onMyButtonClicked(count: number) {
      this.greatText = "こんにちわ";
      this.count = count;
    }
  },
  computed: {
    isRegulars(): boolean {
      return this.count >= 3;
    }
  },
  watch: {
    count(c: number) {
      if (c === 3) {
        alert("常連になりました");
      }
    }
  }
});
</script>
