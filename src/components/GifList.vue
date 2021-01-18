<template>
    <gif v-for="gif in gifs" :gif="gif" :key="gif.id"/>
</template>


<script>
import Gif from './Gif';
export default {
  name: "GifList",
  components:{
      Gif,
  },
  props: ['gifs'],
};
</script>

<style>
</style>