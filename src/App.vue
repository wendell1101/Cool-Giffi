<template>
  <Navbar />
  <div class="container">
    <Search @fetch-data="getData" @query="getQuery"/>
     <h3 class="query" v-if="query">Results for "{{ query }}"</h3>
    <div class="gifs" v-if="gifs.length">
      <GifList :gifs="gifs" />
    </div>
     <h3 class="trending-title" v-if="trending.length && gifs.length === 0 && query.length === 0">Trending</h3>
    <div class="gifs" v-if="trending.length && gifs.length === 0 && query.length === 0">


      <TrendingList :gifs="trending" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Search from "./components/Search";
import GifList from "./components/GifList";
import TrendingList from "./components/TrendingList";
import Navbar from './components/Navbar';

export default {
  name: "App",
  components: {
    Search,
    GifList,
    TrendingList,
    Navbar
  },
  data() {
    return {
      gifs: [],
      trending: [],
      query: '',
    };
  },
  methods: {
    getData(data) {
      this.gifs = data;
    },
    getQuery(q){
      this.query = q;
    }
  },
  created() {
    const apiKey = "n023HKniK2TgdbPfdJZDkzPolgOf8RMW";
    const limit = 12;
    axios
      .get(
        `https://api.giphy.com/v1/gifs/trending?api_key=${apiKey}&limit=${limit}&rating=g`
      )
      .then(res => {
        this.trending = res.data.data;
      })
      .catch(err => console.log(err));
  }
};
</script>

<style>

</style>
