<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoList></VideoList>
    </div>
</template>
    
<script>
import axios from 'axios';
import SearchBar from './components/SearchBar'
import VideoList from './components/VideoList';
const API_KEY = 'AIzaSyDk1v2F8gDJZiFNOQQf2NQN7RwE6Ue0TOI'

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList
    },
    methods: {
        onTermChange: function(searchQuery) {
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchQuery
                }
            }).then(response => console.log(response)).catch(err => console.log(err))
        }
    }
}
</script>