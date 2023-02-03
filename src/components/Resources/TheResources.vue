<template>
  <base-card>
    <base-button
      @click="changeSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
      >Stored resources
    </base-button>
    <base-button
      @click="changeSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add resources
    </base-button>
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource.vue";
export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: "stored-resources",
      storedResources: [
        {
          id: "official-guide",
          title: "Oficial guide",
          description: "The oficial vue.js documintation",
          link: "https://vuejs.org",
        },
        {
          id: "google",
          title: "Google",
          description: "Learn to google...",
          link: "https://google.com",
        },
      ],
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === "stored-resources" ? null : "flat";
    },
    addResButtonMode() {
      return this.selectedTab === "add-resource" ? null : "flat";
    },
  },
  provide() {
    return {
      resources: this.storedResources,
    };
  },
  methods: {
    changeSelectedTab(tab) {
      this.selectedTab = tab;
    },
  },
};
</script>
