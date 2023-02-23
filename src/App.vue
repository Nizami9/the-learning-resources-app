<template>
  <the-header title="RememberMe"></the-header>
</template>

<script>
  import TheHeader from "./components/layout/TheHeader.vue";
export default {
  components: {
  TheHeader
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
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>