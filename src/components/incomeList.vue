<template>
  <div class="income-list">
    <incomeItem v-for="data in state.income" :key="data.ID" :income="data" />
  </div>
</template>

<script>
import incomeItem from "./incomeItem";
export default {
  props: {
    state: Object
  },
  setup() {
    return {
      incomeItem
    };
  }
};
</script>

<style>
</style>