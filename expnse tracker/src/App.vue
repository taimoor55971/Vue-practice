<!-- eslint-disable no-unused-vars -->
<template>
  <HeaderComp :totalIncome=state.totalIncome   />
  <FormComp :state="state" @add-income="AddIncome"/>
  <IncomeList :state="state" @remove-item="removeItem"/>
</template>

<script setup>
// eslint-disable-next-line no-unused-vars
import { reactive, computed } from 'vue';
import HeaderComp from "./components/HeaderComp.vue"
import FormComp from "./components/FormComp.vue"
import IncomeList from './components/IncomeList.vue'
// eslint-disable-next-line no-unused-vars
const state = reactive({
  income: [],
  totalIncome: computed(() => {
    let temp = 0
    if (state.income.length > 0) {
      for (let i = 0; i < state.income.length; i++) {
        temp += state.income[i].value
      }
    }


    return temp
  })



});

const AddIncome = (data) => {
  let d = data.date.split('-')
  let newD = new Date(d[0], d[1], d[2])
  state.income = [...state.income, {
    id: Date.now(),
    desc: data.desc,
    value: parseInt(data.value),
    date:newD.getTime()
    
  }]
  
}

const removeItem = (id) => {
  state.income=state.income.filter(v=>v.id!=id)
}



  


</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Fira Sans', sans-serif;
}

body {
  background-color: #EEE;
}
</style>