<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
        <VideoDetail :video="selectedVideo" />
        <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";
const API_KEY = "AIzaSyBZuRq0zMkqpPmSQvuw2ceunF1HpID1sY0";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data: function() {
    return {
      videos: [],
      selectedVideo : null
    };
  },
  methods: {
      onVideoSelect(video) {
          this.selectedVideo = video;
      },
    onTermChange: function(searchQuery) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchQuery,
          },
        })
        .then((response) => {
          this.videos = response.data.items;
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>
