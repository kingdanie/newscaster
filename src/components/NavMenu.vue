<template>
    <div v-if="notRes">
      Fetching Data.... Please wait.
    </div>
<div>
  <h1>this is the selected {{ selectedKeys }}</h1>
      <a-menu :selectedKeys="selectedKeys" theme="light" mode="inline">
        <RouterLink to="/">
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
      <RouterLink :to="dataSee" >
      Cars
    </RouterLink>
      <RouterLink to="/about">
        <a-menu-item key="3">
          <upload-outlined />
          <span>About</span>
        </a-menu-item>
      </RouterLink>
      <a-menu-item v-for="(navItemzz, index) in navItemz" :key="index">
      <div @click="pushToRoute(navItemzz[0])">{{navItemzz[0]}}</div>
      </a-menu-item>
      </a-menu>

    </div>
  </template>
  <script lang="ts">
    import { RouterLink, RouterView } from 'vue-router'
    import { defineComponent } from 'vue';

  export default defineComponent({
    props: {
      selectedKeys: []
    },
      data: ()=>({
          navItemz: [],
          notRes: false,
          dataSee: {
            name: 'cars',
            params: { username: 'mark2021' } 
          }
    }),
      methods: {
        pushToRoute(item){
          //alert(item)
          this.$router.push({name: 'cars', params: { username: item }})
          //this.$router.push(`/cars/${item}`)
          console.log(this.$route.params)

        },
        async loadMenu() {
        this.notRes = true
        fetch('newspaper-sources.json')
          .then(response => response.json())
          .then(res => {
            this.navItemz = res.details
            this.notRes = false
          }).catch(err=>{console.log(err); //this.$router.push('/');
        location.assign('/')})
    }
    },
      created() {
        this.loadMenu();
      console.log(`the component is now mounted.`);
  
  }
  })
  </script>
  
  
  <style scoped>
  
    </style>
    