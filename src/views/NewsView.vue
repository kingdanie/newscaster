<script setup>
import Articles from '@/components/Articles.vue'
// import Calendar from '@/components/Calendar.vue'
import { useRouter, useRoute } from 'vue-router'
  const router = useRouter()
    const route = useRoute()
  console.log(route.params)
</script>


<!-- <script>
  import { defineComponent } from 'vue'
export default defineComponent({
  props: {
    articleUrl: String,
  },
  mounted() {
    console.log(this.$router)
  },
  methods: {
    getPosts() {
      
    },
  },
})

  </script> -->
<template>
  <div>
    <!-- <Calendar /> -->
    <Articles news-post="Are you there" />
  </div>
</template>
