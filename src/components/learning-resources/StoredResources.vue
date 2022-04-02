<template>
  <ul v-if="resources.length > 0">
    <learning-resource
      v-for="res in resources"
      :id="res.id"
      :key="res.id"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    >
    </learning-resource>
  </ul>

  <base-card v-else :class="{ warn: resourcesIsEmpty }">
    <p><strong>Warning! </strong> no recourses added yet</p>
  </base-card>
</template>

<script>
import LearningResource from './LearningResource.vue';
export default {
  methods: {
    resourcesIsEmpty() {
      return this.resources.length === 0;
    },
  },
  components: {
    LearningResource,
  },
  inject: ['resources'],
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
