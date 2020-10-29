<template>
  <div class="home">
    <p>{{ greetText }}</p>
    <p>挨拶した回数：{{ count }}回</p>
    <p v-if="isRegulars">いつもありがとうございます。</p>
    <p>
      <my-button :greet="greetText" @click="onMyButtonClicked">
        おはこんばんちわ
      </my-button>
    </p>
    <p>
      <reset-button initialValue="はろー" v-model="greetText"> </reset-button>
    </p>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from "vue-property-decorator";
import MyButton from "@/components/MyButton.vue";
import ResetButton from "@/components/ResetButton.vue";

@Component({
  components: {
    MyButton,
    ResetButton
  }
})
export default class Home extends Vue {
  private count = 0;
  public greetText = "Hello";

  public get isRegulars() {
    return this.count >= 5;
  }

  @Watch("count")
  public mt5Times() {
    if (this.count == 10) {
      alert("常連になりました");
    }
  }

  public onMyButtonClicked(count: number) {
    this.greetText = "こんにちは";
    this.count = count;
  }
}
</script>
