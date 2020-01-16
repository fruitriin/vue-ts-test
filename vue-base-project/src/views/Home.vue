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

<script>
// @ is an alias to /src
import MyButton from "@/components/MyButton.vue";
import ResetButton from "@/components/ResetButton.vue";

export default {
  name: "home",
  components: {
    MyButton,
    ResetButton
  },
  data() {
    return {
      greatText: "Hello",
      count: 0
    };
  },
  methods: {
    onMyButtonClicked(count) {
      this.greatText = "こんにちわ";
      this.count = count;
    }
  },
  computed: {
    isRegulars() {
      return this.count >= 3;
    }
  },
  watch: {
    count(c){
      if(c === 3){
        alert("常連になりました")
      }
    }
  }

};
</script>
