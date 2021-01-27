<template>
  <ul class="list-group">
    <VideoListItem
      v-for="(videoObj, index) in videos"
      :key="index"
      :video="videoObj"
    ></VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  components: {
    VideoListItem,
  },
  props: ["videos"],
};
</script>

<style lang="stylus"></style>
