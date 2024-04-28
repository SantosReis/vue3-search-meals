<template>
  <div class="flex p-8 flex-col items-center justify-center">
    <div>
      <input
        type="text"
        class="rounded border-2 border-gray-200 w-72"
        placeholder="Search for Meals"
      />
    </div>

    <div class="flex justify-center gap-2 mt-2">
      <router-link
        :to="{ name: 'byLetter', params: { letter } }"
        v-for="letter of letters.split('')"
      >
        {{ letter }}
      </router-link>
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import store from './../store';
import axiosClient from '../axiosClient';

const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
const ingredients = ref([]);

onMounted(async () => {
  const response = await axiosClient.get('/list.php?i=list');
  console.log(response.data);
  ingredients.value = response.data;
});
</script>
