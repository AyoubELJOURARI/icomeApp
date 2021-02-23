<template>
  <Header :totalIncome="state.totalIn" />
  <Forme @add-Income="addincome" />
  <incomeList :state="state" />
</template>

<script>
import { reactive, computed } from "vue";
import Header from "./components/Header";
import Forme from "./components/Form";
import incomeList from "./components/incomeList";
export default {
  setup() {
    const state = reactive({
      income: [],
      totalIn: computed(() => {
        let temp = 0;
        if (state.income.length > 0) {
          for (let i = 0; i < state.income.length; i++) {
            temp += state.income[i].value;
          }
        }
        return temp;
      })
    });

    function addincome(data) {
      let d = data.date.split("-");
      let newD = new Date(d[0], d[1], d[2]);
      state.income.push({
        ID: Date.now(),
        desc: data.desc,
        value: parseInt(data.value),
        date: newD.getTime()
      });

      console.log(state.income);
    }

    return {
      Header,
      Forme,
      state,
      addincome,
      incomeList
    };
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
}

body {
  background: #0a3d62;
}
</style>
