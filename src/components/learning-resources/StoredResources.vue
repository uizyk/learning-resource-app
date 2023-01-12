<template>
    <ul>
      <learning-resource 
        v-for="res in resources" 
        :key="res.id"
        :title="res.title"
        :description="res.description"
        :link="res.link"
        >
      </learning-resource>
    </ul>
 </template>


<script>
import LearningResource from './LearningResource.vue';

export default {

    inject: ['resources'],

    components: {
        LearningResource
    }
}

</script>

<style scoped>
  ul{
    padding: 0 20px 0 20px;
  }
</style>
  