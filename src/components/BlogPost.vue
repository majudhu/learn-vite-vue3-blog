<template>
  <div>
    <h2 class="text-xl my-3">{{ title }}</h2>
    <img class="w-full" :src="image" />
    <p class="text-gray-700 my-3">
      {{ text }}
      <a class="float-right text-gray-500 border p-1" v-if="!!url" :href="url">Open</a>
    </p>
    <hr class="my-8" />
  </div>
</template>

<script setup>
defineProps({ title: String, text: String, image: String, url: String });
</script>
