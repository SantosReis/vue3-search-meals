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

  <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
    <div
      v-for="meal of meals"
      :key="meal.idMeal"
      class="bg-white shadow rounded-xl"
    >
      <img
        :src="meal.strMealThumb"
        :alt="strMeal"
        class="rounded-t-xl w-full h-48 object-cover"
      />
      <div class="p-3">
        <h3 class="font-bold">{{ meal.strMeal }}</h3>
        <p class="mb-4">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Earum in
          magnam reprehenderit dolores natus assumenda esse possimus sunt
          voluptatem nemo, perspiciatis alias quos corrupti voluptates minus
          veritatis incidunt vero voluptatum.
        </p>
        <div class="flex items-center justify-between">
          <a
            :href="meal.strYoutube"
            target="_blank"
            class="px-3 py-2 rounded border-2 text-white border-orange-600 bg-orange-500 hover:bg-orange-600 transition-colors"
            >Youtube</a
          >
          <router-link
            to="/"
            class="ml-3 px-3 py-2 rounded border-2 border-transparent text-indigo-600 transition-colors"
          >
            View
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted, ref } from 'vue';
import store from '../store';
import { useRoute } from 'vue-router';

const route = useRoute();
const keyword = ref('');
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  store.dispatch('searchMeals', keyword.value);
}

onMounted(() => {
  keyword.value = route.params.name;
  if (keyword.value) {
    searchMeals();
  }
});
</script>
