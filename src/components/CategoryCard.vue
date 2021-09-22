<template>
  <div
    class="category-wrapper"
    v-bind:class="[
      { yellow: title === 'Social' },
      { blue: title === 'Governance' },
    ]"
  >
    <p class="category-heading"><span></span>{{ title }}</p>
    <p v-for="obj in category" v-bind:key="obj.id">
      {{ obj.score }} {{ obj.name }}
    </p>
  </div>
</template>

<script>
export default {
  name: "CategoryCard",
  props: ["category", "title"],
};
</script>

<style scoped>
.category-wrapper {
  background-color: #f5ffee;
  border-radius: 1rem;
  padding: 1rem 1.5rem;
  margin-top: 1rem;
}

.yellow {
  background-color: #fffff1;
}

.blue {
  background-color: #f2f7ff;
}

.category-heading {
  display: flex;
  align-items: center;
}

span {
  height: 1rem;
  width: 1rem;
  background-color: #9fd3a5;
  border-radius: 50%;
  display: inline-block;
  margin: 0 0.3rem 0 0;
}

.yellow span {
  background-color: #f2e888;
}

.blue span {
  background-color: #88bff2;
}
</style>