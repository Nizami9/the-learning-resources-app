<template>
    <base-card>
        <base-button @click="setSelectedTab('stored-resources')" :mode='storedResButtonColor'>Stored Resources</base-button>
        <base-button @click="setSelectedTab('add-resources')" :mode='addResButtonColor'>Add Resource</base-button>
    </base-card>
    <keep-alive>
        <component :is="selectedTab"></component>
    </keep-alive>
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
            resources: this.storedResources,
            addResource: this.addResource,
            removeResource: this.removeResource
        }
    },
    methods: {
        setSelectedTab(tab) {
            this.selectedTab = tab
        },
        addResource(title, description, url) {
        const newResource = {
            id: new Date().toISOString(),
            title: title,
            description: description,
            link: url
        };
        this.storedResources.unshift(newResource);
        this.storedResources = 'stored-resources'
    },
    removeResource(resId) {
        const resIndex = this.storedResources.findIndex((res) => res.id === resId)
        this.storedResources.splice(resIndex, 1)
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