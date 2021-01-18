<template>
    <Trending v-for="gif in gifs" :gif="gif" :key="gif.id"/>
</template>


<script>
import Trending from './Trending';

export default {
  name: "GifList",
  components:{
      Trending
  },
  props: ['gifs'],
};
</script>

<style>
</style>