<template>
    <div class="card-image" @click="showModal">
        <figure class="image is-square">
            <img :src="casts.imgURL" :alt="'Podcast Cover von ' + casts.title" />
        </figure>
    </div>

    <div class="card-content is-clipped" @click="showModal">
        <div class="media">
            <div class="media-content">
                <p class="title is-4">{{ name }}</p>
                <p class="subtitle has-text-grey is-6">{{ casts.author }}</p>
            </div>
        </div>

        <div class="content has-text-left" @click="showModal">{{ casts.description }}</div>

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
        <CardFooter :casts="casts" />
    </footer>



    <!-- Modal -->
    <div class="modal" :class="{ 'is-active': showModalFlag }">
        <div class="modal-background" @click="cancelModal"></div>
        <div class="modal-content">
            <Modal :casts="casts" />
            <button class="modal-close is-large" aria-label="close" @click="cancelModal"></button>
        </div>
    </div>
</template>
    
    
<script>
import axios from "axios";
import Modal from "./Modal.vue";
import CardFooter from "./CardFooter.vue";

export default {
    name: "Card-View",
    components: {
        Modal,
        CardFooter,
    },
    props: ["id", "name", "daten"],

    data() {
        return {
            casts: [],
            showModalFlag: false,
        };
    },

    methods: {
        showModal() {
            this.okPressed = false;
            this.showModalFlag = true;
        },
        cancelModal() {
            this.okPressed = false;
            this.showModalFlag = false;
        },
    },

    async mounted() {
        if (this.id == null) {
            this.casts = this.daten;
            // console.log(this.daten);
        }
        else {
            let result = await axios.get("https://api.fyyd.de/0.2/podcast?podcast_id=" + this.id);
            this.casts = result.data.data;
            // console.log(this.casts);
        }
    },
}
</script>

<style>
.card {
    /* background-color: green; */
    min-height: 50%;
}
</style>