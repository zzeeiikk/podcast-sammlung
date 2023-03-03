<template>
    <PodcastList />
    <Footer />
</template>

<script>
import PodcastList from './components/Podcasts/PodcastList.vue';
import Footer from './components/Footer.vue';

export default {
    name: 'app',
    components: {
        PodcastList,
        Footer,
    }
}

</script>