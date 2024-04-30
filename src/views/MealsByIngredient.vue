<template>
  <div>
    SearchByIngredient
    <pre>{{ ingredients }}</pre>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import axiosClient from '../axiosClient';

const ingredients = ref([]);

onMounted(() => {
  axiosClient.get('list.php?i=list').then(({ data }) => {
    // debugger;
    ingredients.value = data;
  });
});
</script>
