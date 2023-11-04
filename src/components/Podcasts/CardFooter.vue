<template>
    
  <a v-for="tags in casts.categories" :key="tags" href="#" class="card-footer-item">{{ tags }}</a>

</template>
    
    
<script>
import axios from "axios";

export default {
    name: "CardFooter",

    data() {
        return {
            showModalFlag: false,
        };
    },

    props: ["casts"],

    categories: function () {
    axios
      .get("categories.json")
      .then((res) => {
        this.cat = res.data
        console.log(this.cat)
      }
    )
  },

}
</script>

