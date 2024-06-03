<template>
  <div class="container mx-auto max-w-screen-xl px-4 py-8">
    <div class="mb-4">
      <router-link to="/" class="text-blue-500 hover:underline flex items-center">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 mr-1" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7 7-7m8 14l-7-7 7-7" />
        </svg>
        Back to Projects
      </router-link>
    </div>
    <div class="bg-white shadow-lg rounded-lg overflow-hidden">
      <figure class="w-full flex max-w-screen-xl">
        <img 
          v-for="img in project.image"
          :src="img"
          alt="Project image"
          class="w-full h-64 object-contain cursor-pointer"
          :title="img"
          @click="openImage(img)"
        />
      </figure>
      <div class="p-8">
        <h1 class="text-3xl font-bold mb-4">{{ project.name }}</h1>
        <p class="text-gray-600">{{ project.description }}</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { useRoute } from 'vue-router'

interface Project {
  id: number;
  name: string;
  image: string[];
  description: string;
  link?: string;
}

export default defineComponent({
  name: 'ProjectDetail',
  data() {
    return {
      projects: [
        { 
          id: 1,
          name: 'CRUD Cars',
          image: 'link-to-image-1.jpg',
          description: 'project made with Android XML for car management CRUD. It allows you to create, read, update, and delete cars and storing them in a SQLite database.',
          link: 'https://github.com/paulohfsantos/crud-kotlin-cars'
        },
        {
          id: 2,
          name: 'One Tap Signin',
          image: [
            '/ss1.png',
            '/ss2.png'
          ],
          description: 'Signin handler with a google button made with jetpack compose. It allows users to signin with their google account with a single tap. Made with SDK/API 34 and Android 13'
        },
        {
          id: 3,
          name: 'Finance Manager',
          image: 'link-to-image-3.jpg',
          description: 'OCR-based App for information scanning. Made with Jetpack Compose and ML-Kit, it allows users to scan and extract information from receipts, invoices, and other documents.'
        },
      ] as Project[],
      project: {} as Project
    }
  },
  methods: {
    openImage(img: string) {
      window.open(img, '_blank')
    }
  },
  created() {
    const route = useRoute()
    const projectId = Number(route.params.id)
    this.project = this.projects.find(project => project.id === projectId) as Project
  }
})
</script>
