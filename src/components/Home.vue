<template>
  <div class="container mx-auto max-w-screen-xl px-4 py-8">
    <h1 class="text-4xl font-bold mb-8 text-center">My Android Projects</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <div v-for="project in projects" :key="project.id"
        class="bg-white shadow-lg rounded-lg overflow-hidden transition transform hover:-translate-y-1 hover:shadow-2xl">
        <router-link :to="'/project/' + project.id" class="block">
          <img :src="project.image" alt="Project image" class="w-full h-48 object-cover">
          <div class="p-4">
            <h2 class="text-xl font-semibold">{{ project.name }}</h2>
            <p class="text-gray-600 mt-2">{{ project.shortDescription }}</p>
          </div>
        </router-link>
        <div class="p-4 border-t border-gray-200">
          <a v-if="project.apkUrl" :href="project.apkUrl" class="text-blue-500 hover:underline" download>
            Download APK
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

interface Project {
  id: number;
  name: string;
  image: string;
  shortDescription: string;
  apkUrl?: string;
}

export default defineComponent({
  name: 'Home',
  data() {
    return {
      projects: [
        { id: 1, name: 'CRUD Cars', shortDescription: 'Car management CRUD made with Android XML', image: '' },
        { id: 2, name: 'One Tap Signin', shortDescription: 'Signin handler with a google button made with jetpack compose', image: '' },
        { id: 3, name: 'Finance Manager', shortDescription: 'OCR-based App for information scanning', image: '' }
      ] as Project[]
    }
  }
})
</script>
