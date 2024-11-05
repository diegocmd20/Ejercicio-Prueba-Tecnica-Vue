<template>
    <div class="container">
        <label class="form-label display-5">Raza de Perro</label>
        <select class="form-select my-2" v-model="selectedBreed" @change="onSelectedBreed">
            <option selected>Selecciona una raza</option>
            <option v-for="breed in breeds" :value="breed" :key="breed">{{ breed }}</option>
        </select>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'BreedSelector',
    data() {
        return {
            selectedBreed: '',
            breeds: [],
        };
    }, async mounted() {
        try {
            const url = 'https://dog.ceo/api/breeds/list/all';
            const { data } = await axios.get(url);
            console.log(data);
            this.breeds = Object.keys(data.message);
        }
        catch (error) {
            console.error('Error fetching breeds: ', error);
        }
    },
    methods:
    {
        onSelectedBreed() {
            this.$emit('selectedBreed', this.selectedBreed)
        }
    }
};
</script>

<style scoped></style>