<template>
  <li class="list-group-item media">
    <img class="m-3" :src="thumbnailUrl" />
    <div class="media-body m-3">
      {{ video.snippet.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
};
</script>


<style scoped>

li {
    display: flex;
    cursor: pointer;
}

li:hover {
    background-color : #eee;
}
</style>