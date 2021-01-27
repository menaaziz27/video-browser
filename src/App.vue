<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList :videos="videos"></VideoList>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
const API_KEY = "AIzaSyBZuRq0zMkqpPmSQvuw2ceunF1HpID1sY0";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
  },
  data: function() {
    return {
      videos: [],
    };
  },
  methods: {
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
