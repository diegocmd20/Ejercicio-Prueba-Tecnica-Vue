<template>
    <div>
        <li v-for="breedImage in breedImages" :value="breedImage" :key="breedImage">{{ breedImage }}</li>
    </div>
</template>

<script>
import axios from 'axios';
import BreedSelector from './BreedSelector.vue';
export default {
    name: 'DogGallery',
    props: ['selectedBreed'],
    components: {
        BreedSelector,
    },
    data() {
        return {
            breedImages: [],
        };
    },
    methods: {
        async fetchImage(selectedBreed){
            try {
                const url = `https://dog.ceo/api/breed/${selectedBreed}/images/random/6`;
                const { data } = await axios.get(url);
                console.log(data);
                this.breedImages = data;
            }
            catch (error) {
                console.error('Error fetching images: ', error)
            }
        }
    }
    ,
    watch: {
        selectedBreed(newBreed) {
            if (newBreed) {
                this.fetchImage(newBreed);
                console.log("Selected breed:", newBreed);
            }
        }
    }
};
</script>

<style scoped></style>