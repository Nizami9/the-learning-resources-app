<template>
    <base-card>
        <base-button @click="setSelectedTab('stored-resources')" :mode='storedResButtonColor'>Stored Resources</base-button>
        <base-button @click="setSelectedTab('add-resources')" :mode='addResButtonColor'>Add Resource</base-button>
    </base-card>
    <component :is="selectedTab"></component>
</template>

<script>
  import StoredResources from "./StoredResources.vue"
  import AddResources from "./AddResources.vue"

export default{
    components: {StoredResources, AddResources},
    data() {
        return {
            selectedTab: 'stored-resources',
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
    },
    provide() {
        return {
            resources: this.storedResources
        }
    },
    methods: {
        setSelectedTab(tab) {
            this.selectedTab = tab
        }
    },
    computed: {
        storedResButtonColor() {
            return this.selectedTab === 'stored-resources' ? null : 'flat';
        },
        addResButtonColor() {
            return this.selectedTab === 'add-resources' ? null : 'flat';
    }
}
}
</script>