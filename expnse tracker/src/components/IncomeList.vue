<template>
  <div class="income-list"><h1>List</h1>
  <IncomeItem v-for = ' data in state.income'  :key="data.id" :income="data" @remove-item="removeItem" />
  </div>
</template>

<script setup>
import { defineProps,defineEmits } from 'vue';
import IncomeItem from "./IncomeItem.vue"
// eslint-disable-next-line no-unused-vars
const props = defineProps({
    state: {
        type:Object
    }
})
const emit=defineEmits('remove-item')
function removeItem(id) {
    emit('remove-item', id);
}

</script>

<style scoped>
.income-list{
    margin-top: 30px;
    padding: 15px;
}
</style>