<template>
  <div class="home">
    <p>{{ state.greatText }}</p>
    <p>挨拶した回数 : {{ state.count }}回</p>
    <p v-if="isRegulars">いつもありがとうございます</p>
    <p>
      <MyButton :great="state.greatText" @click="onMyButtonClicked" />
    </p>
    <p>
      <ResetButton initialValue="Hello" v-model="state.greatText" />
    </p>
  </div>
</template>

<script lang="ts">
import {
  createComponent,
  reactive,
  ref,
  computed,
  watch
} from "@vue/composition-api";

// @ is an alias to /src
import MyButton from "@/components/MyButton.vue";
import ResetButton from "@/components/ResetButton.vue";

export default createComponent({
  setup() {
    const state = reactive({
      greatText: "Hello",
      count: 0
    });
    const greatText2 = ref("Hello");
    const onMyButtonClicked = (count: number) => {
      state.greatText = "こんにちわ";
      state.count = count;
    };
    const isRegulars = computed(() => {
      return state.count >= 3;
    });
    watch(
      () => state.count,
      () => {
        if (state.count === 3) {
          alert("常連になりました");
        }
      }
    );
    return {
      state,
      onMyButtonClicked,
      isRegulars
    };
  },
  components: {
    MyButton,
    ResetButton
  }
});
</script>
