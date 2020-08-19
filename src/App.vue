<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo"></VideoDetail>
      <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from "./components/SearchBar.vue";
import VideoList from "./components/VideoList.vue";
import VideoDetail from "./components/VideoDetail.vue";

const API_KEY = "AIzaSyCBBA9l_hflrlyaCsz3nErT0nZiTKaNf5g";

export default {
  name:"App",
  components:{
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos:[],
      selectedVideo:null
    }
  },
  methods:{
    onTermChange(searchTerm) {
      axios.get("https://www.googleapis.com/youtube/v3/search", {
        params:{
          key:API_KEY,
          type:'video',
          part:'snippet',
          q:searchTerm
        }
      }).then(response => {
        this.videos = response.data.items
      });
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
}
</script>

