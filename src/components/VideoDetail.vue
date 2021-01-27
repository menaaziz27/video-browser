<template>
    <div v-if="video" class="col-md-8">
        <div class="resp-container">
            <iframe class="resp-iframe" :src="videoUrl" />
        </div>
        <div class="details">
        <h4>{{ video.snippet.title }}</h4>
        {{ video.snippet.description }}
        </div>
    </div>
</template>


<script>
export default {
    name: 'VideoDetail',
    props: ['video'],
    computed: {
        videoUrl() {
            const { videoId } = this.video.id;
            return `https://www.youtube.com/embed/${videoId}`;
        }
    }
}
</script>


<style scoped>

.details{
    padding: 10 px;
    margin-top : 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
}

.resp-container {
    position: relative;
    overflow: hidden;
    padding-top: 56.25%;
}

.resp-iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: 0;
}
</style>
