<template>
  <div id="app">
    <div class="wrapper">
      <h1>ESG Scoring</h1>
      <p>This is a list of top 5 companies in each ESG category</p>
      <div class="category-wrapper">
        <p class="category-heading"><span></span>Category</p>
        <p v-for="obj in info" v-bind:key="obj.id">
          {{ obj.score }} {{ obj.name }} {{ obj.categories }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",

  data() {
    return {
      info: null
    };
  },
  mounted() {
    axios
      .get("https://api.acty.se/")
      .then((response) => (this.info = response.data));
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
  max-width: 37.5rem;
  margin: auto;
  padding-top: 1.5rem;
}

h1 {
  font-size: 1.125rem;
  padding-bottom: 0.5rem;
}

p {
  font-size: 0.88rem;
  line-height: 1.5rem;
}


.category-heading {
  display: flex;
  align-items: center;
}

span {
  height: 1rem;
  width: 1rem;
  background-color: #9FD3A5;
  border-radius: 50%;
  display: inline-block;
  margin: 0 .3rem 0 0;
}


.category-wrapper {
  background-color: #f5ffee;
  border-radius: 1rem;
  padding: 1rem 1.5rem;
  margin-top: 1rem;
}




</style>
