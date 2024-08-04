<script setup>
import { defineProps } from "vue";
import { RouterLink } from "vue-router";

defineProps({
  bg: {
    type: String,
    default: "bg-gray-100",
  },
  title: {
    type: String,
    default: "For Developers",
  },
  description: {
    type: String,
    default: "Browse our Vue jobs and start your career today",
  },
  link: {
    type: String,
    default: "/jobs",
  },
  linkText: {
    type: String,
    default: "Browse Jobs",
  },
  buttonColor: {
    type: String,
    default: "bg-black",
  },
});
</script>

<template>
  <div :class="`${bg} p-6 rounded-lg shadow-md`">
    <h2 class="text-2xl font-bold">{{ title }}</h2>
    <p class="mt-2 mb-4">{{ description }}</p>
    <RouterLink
      :to="`${link}`"
      :class="`inline-block ${buttonColor} text-white rounded-lg px-4 py-2 hover:bg-gray-700`"
    >
      {{ linkText }}
    </RouterLink>
  </div>
</template>
