<template>
  <div class="section">
    <div class="container">
      <h1 class="title is-1">Podcast Sammlung</h1>

      <!-- TOP -->
      <div class="columns is-multiline">
        <div v-for="id in ids" :key="id" class="column is-half-tablet is-one-third-desktop is-one-quarter-fullhd">

          <div class="card has-text-left bm--card-equal-height" @click="showModal">

            <top :id="id.id" :name="id.title" :daten="id" />

          </div>
        </div>
      </div>


      <!-- Card -->
      <div class="columns is-multiline">
        <div v-for="id in ids" :key="id" class="column is-half-tablet is-one-third-desktop is-one-quarter-fullhd">

          <div class="card has-text-left bm--card-equal-height" @click="showModal">

            <Card :id="id.id" :name="id.title" :daten="id" />

          </div>
        </div>
      </div>






    </div>
  </div>
</template>
  
  
<script>
import axios from "axios";
import Card from "./Card.vue";
import top from "./top.vue";

export default {
  name: "Podcast-List",
  components: {
    Card,
    top,
  },

  data() {
    return {
      ids: null,
      showModalFlag: false,
    };
  },

  created: function () {
    axios
      .get("id.json")
      .then((res) => {
        this.ids = res.data
      })
  },




}
</script>
  
<style scoped>
.bm--card-equal-height {
  display: flex;
  flex-direction: column;
  height: 80vh;
  overflow: hidden;
}

.bm--card-equal-height .card-footer {
  margin-top: auto;
}
</style>