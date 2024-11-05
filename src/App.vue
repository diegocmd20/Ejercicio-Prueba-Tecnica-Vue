<script>
import BreedSelector from './components/BreedSelector.vue';
import DogGallery from './components/DogGallery.vue';
export default {
  name: 'App',
  components: {
    BreedSelector, DogGallery,
  },
  data() {
    return {
      selected: ''
    };
  },
  methods: {
    handleBreed(breed) {
      this.selected = breed;
    }
  }
}

</script>

<template>
  <div>
    <BreedSelector @selectedBreed="handleBreed" />
    <DogGallery :selectedBreed="selected" />
  </div>
</template>

<style scoped>
</style>
