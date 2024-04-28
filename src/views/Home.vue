<template>
  <pre>{{ meals }}</pre>
</template>

<script setup>
// import { computed } from 'vuex/types/helpers.js';
// import { computed } from '@vue/reactivity';
import { computed } from 'vue';
import store from './../store'

const meals = computed(() => store.state.meals)
</script>