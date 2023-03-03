<template>
    <div class="card">
    <div class="card-image">
        <figure class="image is-square">
            <img :src="casts.imgURL" :alt="'Podcast Cover von ' + casts.title" />
        </figure>
    </div>

    <div class="card-content is-clipped">
        <div class="media">
            <div class="media-content">
                <p class="title is-4">{{ casts.name }}</p>
                <p class="subtitle has-text-grey is-6">{{ casts.author }}</p>
            </div>
        </div>

        <div class="content has-text-left">{{ casts.description }}</div>

        <a :href="casts.htmlURL" target="_blank">
            <button class="button">
                <i class="fas fa-command"></i> Website
            </button>
        </a>

        <a :href="casts.xmlURL" target="_blank">
            <button class="button is-info is-pulled-right">
                <i class="fas fa-podcast"></i> Abonnieren
            </button>
        </a>

    </div>

    <footer class="card-footer is-flex-wrap-wrap">
        <a v-for="tags in casts.categories" :key="tags" href="#" class="card-footer-item">{{ tags }}</a>
    </footer>
    <button class="modal-close is-large" aria-label="close" @click="cancelModal"></button>
    </div>
</template>
    
    
<script>
// import axios from "axios";

export default {
    name: "Modal-View",
    props: ["casts"],

    data() {
        return {
            showModalFlag: false,
        };
    },
}
</script>

