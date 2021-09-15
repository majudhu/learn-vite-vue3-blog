<template>
  <div class="max-w-md mx-auto">
    <h1 class="text-3xl font-bold my-4">Welcome to Learn Vue 3 Blog</h1>

    <BlogPost
      v-for="p in posts"
      :key="p.title"
      :title="p.title"
      :text="p.text"
      :image="p.image"
      :url="p.url"
    />

    <BlogPostCreateForm :posts="posts" @addPost="addPost" />
  </div>
</template>

<script setup>
import { reactive } from "vue";
import SAMPLE_POSTS from "./assets/sample_posts.json";
import BlogPost from "./components/BlogPost.vue";
import BlogPostCreateForm from "./components/BlogPostCreateForm.vue";

const posts = reactive(SAMPLE_POSTS);
const addPost = (title, text, image, url) =>
  posts.push({ title, text, image, url });
</script>

<style>
@tailwind base;
@tailwind components;
@tailwind utilities;
</style>
