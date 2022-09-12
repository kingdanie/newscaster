<script>
  import { defineComponent } from 'vue'
export default defineComponent({
  props: {
    newsPost: String,
  },
  mounted() {
    this.newsPost
  },
  methods: {
    pickaboo() {
      alert("I see you");
    },
  },
})
</script>

<template>
  <h1>Component Work!</h1>
  <p>{{ newsPost }}</p>
  <h2>What is going on here!</h2>
  <a-button @click="pickaboo">primary</a-button>
</template>


