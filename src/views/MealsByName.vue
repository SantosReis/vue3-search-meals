<template>
  <div class="flex p-8 flex-col items-center justify-center">
    <input
      type="text"
      v-model="keyword"
      class="rounded border-2 border-gray-200 w-72"
      placeholder="Search for Meals"
      @change="searchMeals"
    />
  </div>
  <pre>{{ meals }}</pre>
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { ref } from 'vue';
import store from '../store';

const keyword = ref('');
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  store.dispatch('searchMeals', keyword.value);
}
</script>
