<template>
    <!-- <div v-if="notRes">
      Fetching Data.... Please wait.
    </div> -->
<div>
      <a-menu v-model:selectedKeys="selectedKeys" theme="light" mode="inline">
        <RouterLink to="/home">
        <a-menu-item key="1">
          <user-outlined />
          <span>Documentation</span>
        </a-menu-item>
      </RouterLink>
      <RouterLink to="/news">
        <a-menu-item key="2">
          <video-camera-outlined />
          <span>News</span>
        </a-menu-item>          
      </RouterLink>
      <RouterLink to="/about">
        <a-menu-item key="3">
          <upload-outlined />
          <span>About</span>
        </a-menu-item>
      </RouterLink>
      <a-menu-item v-for="(navItemzz, index) in navItemz" :key="index">
      <RouterLink :to='navItemzz[1]'>{{navItemzz[0]}}</RouterLink>
      </a-menu-item>
      </a-menu>

    </div>
  </template>
  <script lang="ts">
    import { RouterLink, RouterView } from 'vue-router'
    import { defineComponent } from 'vue';

  export default defineComponent({
      data: ()=>({
          navItemz: [],
          notRes: false,
    }),
      methods: {
        async loadMenu() {
        this.notRes = true
        fetch('newspaper-sources.json')
          .then(response => response.json())
          .then(res => {
            this.navItemz = res.details
            this.notRes = false
          })
    }
    },
      mounted() {
        this.loadMenu();
      console.log(`the component is now mounted.`);
  
  }
  })
  </script>
  
  
  <style scoped>
  
    </style>
    