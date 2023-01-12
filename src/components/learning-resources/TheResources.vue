<template>

    <base-card>
        <base-button @click="setSelectedTab('stored-resources')" :mode="storedResButtonMode">Stored Resources</base-button>
        <base-button @click="setSelectedTab('add-resources')" :mode="addResButtonMode" >Add Resource Resources</base-button>
    </base-card>
    <base-card>
      <stored-resources v-if="selectedTab === 'stored-resources'"></stored-resources>
      <keep-alive>
        <add-resources v-if="selectedTab === 'add-resources'"></add-resources>
      </keep-alive>
    </base-card>

</template>


<script>

import StoredResources from './StoredResources.vue';
import AddResources from './AddResource.vue';

export default {
    components: {
        StoredResources,
        AddResources
    },
    
  data() {
    return {
      selectedTab: "stored-resources",
      storedResources: [
        {
          id: "official-guide",
          title: "Official Guide",
          description: "The Official Vue.js documentation.",
          link: "https://vuejs.org",
        },
        {
          id: "google",
          title: "Google",
          description: "Learn to google.. ",
          link: "https://google.com",
        },
      ],
    };
  },
  provide() {
    return{
        resources: this.storedResources,
        addResource: this.addResource
    }
  },

  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url){
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url
      }
      this.storedResources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    }
  },
  computed: {
    storedResButtonMode(){
      return this.selectedTab === 'stored-resources' ? null : 'flat'
    },
    addResButtonMode(){
      return this.selectedTab === 'add-resources' ? null : 'flat'
    }
  }
};
</script>


