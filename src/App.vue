<template>
  <ul>
  <learning-resource :key="res.id" 
  v-for="res in storedResources"
  :title="res.title"
  :description="res.description"
  :link="res.link"></learning-resource>
</ul>
</template>

<script>
  import LearningResource from "./components/learning-resources/LearningResource.vue"
export default {
  components: {
    LearningResource
  },
  data() {
    return {
      storedResources: [
        {
          id: 'google',
          title: 'Google',
          description: 'Learn how to google',
          link: 'https://google.com'
        },
        {
          id: 'official-guide',
          title: 'Official Guide',
          description: 'The official Vue.js documentation',
          link: 'https://vuejs.org'
        }
      ]
    }
  }
}
</script>

<style>
</style>
