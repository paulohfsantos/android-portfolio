<template>
  <div class="container mx-auto px-4 py-8">
    <div class="bg-white shadow-lg rounded-lg overflow-hidden">
      <img :src="project.image" alt="Project image" class="w-full h-64 object-cover">
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
  image: string;
  description: string;
}

export default defineComponent({
  name: 'ProjectDetail',
  data() {
    return {
      projects: [
        { id: 1, name: 'Project 1', image: 'link-to-image-1.jpg', description: 'Description of project 1' },
        { id: 2, name: 'Project 2', image: 'link-to-image-2.jpg', description: 'Description of project 2' },
        // Add more projects as needed
      ] as Project[],
      project: {} as Project
    }
  },
  created() {
    const route = useRoute()
    const projectId = Number(route.params.id)
    this.project = this.projects.find(project => project.id === projectId) as Project
  }
})
</script>
