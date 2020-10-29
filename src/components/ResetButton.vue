<template>
  <button @click="onClick">Reset</button>
</template>

<script lang="ts">
import { Component, Prop, Emit, Vue } from "vue-property-decorator";

@Component
export default class ResetButton extends Vue {
  private initialValue!: string;

  @Prop()
  public value!: string;

  @Emit()
  public input(value: string) {
    console.log(value);
  }

  public created() {
    console.log(this.value);
    this.initialValue = this.value;
  }

  public onClick() {
    this.input(this.initialValue);
  }
}
</script>
