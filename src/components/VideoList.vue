<template>
  <ul class="list-group col-md-4 video-list">
    <VideoListItem 
      v-for="video in videos" 
      :video="video" 
      :key="video.etag"
      @videoSelect="onVideoSelect"
    ></VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem.vue"

export default {
  name:"VideoList",
  props:['videos'],
  components:{
    VideoListItem
  },
  methods:{
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    }
  }
}
</script>

<style scoped>
.video-list {
  margin: 10px;
  display:none
}
</style>




