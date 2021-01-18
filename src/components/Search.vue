<template>
    <div class="search">
        <input type="text" name="search" id="search" @input="searching" v-model="query"
        placeholder="Search all GIFS and Stickers">
        <i class="fas fa-search"></i>
    </div>

</template>

<script>
import axios from 'axios';

export default {
    name: 'Search',
    emits: ['fetch-data'],
    data() {
        return{
            gifs: [],
            query: '',
            timeout: null,
        }
    },
    methods:{
        searching() {
            clearTimeout(this.timeout);
            this.timeout = setTimeout(()=>{
                this.onSearch();
            },1000);
        },
        onSearch() {
            const apiKey = "n023HKniK2TgdbPfdJZDkzPolgOf8RMW";
            const limit = 9;
            axios.get(`https://api.giphy.com/v1/gifs/search?api_key=${apiKey}&q=${this.query}&limit=${limit}`)
            .then(res => {
                console.log(res.data.data);
                this.$emit('query', this.query);
                this.$emit('fetch-data', res.data.data);
            })
            .catch(err => console.log(err));
        }
    }
}
</script>

<style>

</style>