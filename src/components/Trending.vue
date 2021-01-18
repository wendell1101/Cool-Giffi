<template>
  <div class="gif-container">
    <img :src="gif.images.original.url" alt="gif/sticker" />
    <div class="copy-container">
      <input ref="url" type="text" readonly :value="gif.images.original.url" />
      <a class="btn-copy"  href="#" @click="copy()">Copy</a>
    </div>
  </div>
  <!-- <pre>{{ gif.images.fixed_width.url }}</pre> -->
</template>


<script>
export default {
  name: "Trending",
  props: ["gif"],
  methods: {
    copy() {
      this.$refs.url.select();
      this.$refs.url.setSelectionRange(0, 99999); /*For mobile devices*/
      /* Copy the text inside the text field */
      document.execCommand("copy");
      alert("Link Copied!");
    }
  }
};
</script>

<style>
</style>