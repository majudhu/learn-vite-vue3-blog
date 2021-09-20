<template>
  <form @submit.prevent="submitForm" class="text-center bg-gray-200 p-3">
    <h2 class="text-2xl text-center text-gray-700">Add a blog post</h2>
    <div class="border py-2">
      <label class="flex text-gray-600">
        Title:
        <input class="ml-2 flex-grow bg-white" v-model="formData.title" required />
      </label>
      <span v-if="titleNotUnique" class="text-red-500">Title not unique</span>
    </div>
    <div class="border py-2">
      <label class="flex text-gray-600">
        Text:
        <input class="ml-2 flex-grow bg-white" v-model="formData.text" required />
      </label>
    </div>
    <div class="border py-2">
      <label class="flex text-gray-600">
        Image:
        <input class="ml-2 flex-grow bg-white" v-model="formData.image" />
      </label>
    </div>
    <div class="border py-2">
      <label class="flex text-gray-600">
        URL:
        <input class="ml-2 flex-grow bg-white" v-model="formData.url" />
      </label>
    </div>
    <button
      class="border border-2 bg-white font-bold my-2 py-1 px-4 font-md"
      :class="{ 'opacity-40': titleNotUnique }"
      type="submit"
      :disabled="titleNotUnique"
    >ADD POST</button>
  </form>
</template>

<script setup>
import { computed, reactive } from "vue";

const props = defineProps({ posts: Array });
const emit = defineEmits(["addPost"]);

const formData = reactive({ title: "", text: "", image: "", url: "" });

const titleNotUnique = computed(() =>
  props.posts.some(
    (p) => p.title.trim().toLowerCase() == formData.title.trim().toLowerCase()
  )
);

function submitForm() {
  emit('addPost', formData.title, formData.text, formData.image, formData.url);
  formData.title = formData.text = formData.image = formData.url = "";
}
</script>
