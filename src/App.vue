<template>
  <ul>
    <resource-item
      v-for="res in storedResources"
      :key="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    ></resource-item>
  </ul>
</template>

<script>
import ResourceItem from "./components/Resources/ResourceItem.vue";
export default {
  components: {
    ResourceItem,
  },
  data() {
    return {
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
};
</script>
