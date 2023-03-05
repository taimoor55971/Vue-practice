<template>
  <div class="income-item">
    <div class="removeItem" @click="removeItem">x</div>
      <div class="desc">
          {{ income.desc }}
        </div>    <div class="price">{{ income.value }}</div>
    <div class="date">{{formateDate}}</div>
  </div>
</template>

<script setup>
import { defineProps,defineEmits } from 'vue';


// eslint-disable-next-line no-unused-vars
const props = defineProps({
    income: {
    type: Object,

    }
    
})
let remove_emit =defineEmits(['remove-item'])
const removeItem = () => {
    remove_emit("remove-item",props.income.id)
}



let date = new Date(props.income.date)
let day = date.getDay()
let month = date.getMonth()
let year = date.getFullYear()
let formateDate=day+'/'+month+'/'+year


</script>

<style>
.income-item {
    position: relative;
    display: flex;
    padding: 15px 15px 15px 0px;
    background-color: #FFF;
    border-radius: 8px;
    max-width: 600px;
    margin: 0 auto 30px;
  }
  .removeItem {
    color: #EF2D2D;
    font-weight: 600;
    font-size: 20px;
    line-height: 1;
    text-align: center;
    margin: 0 15px;
  }
  .desc {
    color: #666;
    flex: 1 1 100%;
    font-size: 20px;
  }
  .price {
    color: #666;
    min-width: 100px;
    font-size: 20px;
  }
  .date {
    color: #666;
    text-align: right;
    font-size: 20px;
  }
</style>