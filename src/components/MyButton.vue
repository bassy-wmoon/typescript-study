<template>
  <button @click="onClick">
    <slot></slot>
  </button>
</template>

<script lang="ts">
import { Component, Prop, Emit, Vue } from "vue-property-decorator";

@Component
export default class MyButton extends Vue {
  private count = 0;

  @Prop()
  public greet?: string;

  @Emit()
  public click(count: number) {
    console.log(count);
  }

  public onClick() {
    alert(this.greet);
    this.count++;
    this.click(this.count);
  }
}
</script>
