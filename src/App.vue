<template>
  <div id="app">
    <div class="wrapper">
      <h1>ESG Scoring</h1>
      <p>This is a list of top 5 companies in each ESG category</p>
      <category-card v-bind:category="environmental" title="Environmental" />
      <category-card v-bind:category="social" title="Social" />
      <category-card v-bind:category="governance" title="Governance" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import CategoryCard from "./components/CategoryCard.vue";

export default {
  components: { CategoryCard },
  name: "App",

  data() {
    return {
      environmental: [],
      social: [],
      governance: [],
    };
  },
  mounted() {
    axios
      .get("https://api.acty.se/")
      .then((response) => {
        const arrayOfObjects = response.data;

        //filter by each category, then sort by score(highest to lowest)
        this.environmental = arrayOfObjects.filter(
          (obj) => obj.categories === "Environmental"
        );
        this.environmental.sort((a, b) => b.score - a.score);

        this.social = arrayOfObjects.filter(
          (obj) => obj.categories === "Social"
        );
        this.social.sort((a, b) => b.score - a.score);

        this.governance = arrayOfObjects.filter(
          (obj) => obj.categories === "Governance"
        );
        this.governance.sort((a, b) => b.score - a.score);
      })
      .catch((error) => console.error(error));
  },
};
</script>

<style>
* {
  font-family: Montserrat, Helvetica, Arial, sans-serif;
  font-weight: 400;
  margin: 0;
  padding: 0;
}

.wrapper {
  width: 37.5rem;
  max-width: 90vw;
  margin: auto;
  padding-top: 1.5rem;
  display: flex;
  flex-direction: column;
}

h1 {
  font-size: 1.125rem;
  padding-bottom: 0.5rem;
}

p {
  font-size: 0.88rem;
  line-height: 1.5rem;
}
</style>
