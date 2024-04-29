<template>
  <div class="bg-white shadow rounded-xl">
    <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
      <img
        :src="meal.strMealThumb"
        :alt="meal.strMeal"
        class="rounded-t-xl w-full h-48 object-cover"
      />
    </router-link>
    <div class="p-3">
      <h3 class="font-bold">{{ meal.strMeal }}</h3>
      <p class="mb-4">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Earum in magnam
        reprehenderit dolores natus assumenda esse possimus sunt voluptatem
        nemo, perspiciatis alias quos corrupti voluptates minus veritatis
        incidunt vero voluptatum.
      </p>
      <div class="flex items-center justify-between">
        <YouTubeButton :href="meal.strYoutube" />
        <router-link
          to="/"
          class="ml-3 px-3 py-2 rounded border-2 border-transparent text-indigo-600 transition-colors"
        >
          View
        </router-link>
      </div>
    </div>
  </div>
</template>

<script setup>
import YouTubeButton from '../components/YouTubeButton.vue';

const { meal } = defineProps({
  meal: {
    required: true,
    type: Object,
  },
});
</script>
