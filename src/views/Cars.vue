<template>
    <div class="profile">
      Car Info
    </div>
    <span>
       Here it is {{ $route.params.username }}
    </span>
  </template> 

<script setup lang="ts">
  import TheWelcome from '../components/TheWelcome.vue'
  </script>