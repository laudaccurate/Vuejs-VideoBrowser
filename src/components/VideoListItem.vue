<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <img :src="thumbnail" class="mr-1" alt="img" >
    <div class="media-body">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name:"VideoListItem",
  props:['video'],
  computed: {
    thumbnail() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit("videoSelect", this.video);
    }
  }
}
</script>

<style scoped>
  li {
    display: flex;
    cursor: pointer;
    align-items: center;
  }

  li:hover {
    background-color: #eee;
  }
</style>


