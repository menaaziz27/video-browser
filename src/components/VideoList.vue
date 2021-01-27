<template>
  <ul class="list-group col-md-4">
    <VideoListItem
      v-for="(videoObj, index) in videos"
      :key="index"
      :video="videoObj"
      @videoSelect="onVideoSelect"
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
  methods: {
      onVideoSelect(video) {
          this.$emit('videoSelect', video);
      }
  }
};
</script>

<style lang="stylus"></style>
