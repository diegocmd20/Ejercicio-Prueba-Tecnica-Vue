<template>
    <div class="row g-4 my-2">
        <div v-for="breedImage in breedImages" :key="breedImage" class="col-md-4">
            <div class="h-100">
                <img :src="breedImage" alt="dog-image" class="card-img-top"  style="height: 250px; object-fit: cover">
            </div>
        </div>
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
        async fetchImage(selectedBreed) {
            try {
                const url = `https://dog.ceo/api/breed/${selectedBreed}/images/random/6`;
                const { data } = await axios.get(url);
                console.log(data);
                this.breedImages = data.message;
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