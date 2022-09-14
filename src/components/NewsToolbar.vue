<template>
  <div v-if="isLoading">Fetching Data.... Please wait.</div>

  <section v-else>
    <!-- <nav v-for="(menuItem, index) in menuItems" :key="index">
       
        <RouterLink :to='menuItem[1]'>{{menuItem[0]}}</RouterLink>
         {{menuItem[0]}}
    </nav> -->
    <a-tabs mode="left" :style="{ minHeight: '40px', fontSize: '12px' }">
      <a-tab-pane
        v-for="(menuItem, index) in menuItems"
        :key="index"
        :tab="`${menuItem[0]}`"
      >
        <!-- <h1>{{ menuItem[0] }}</h1> -->
        <!-- <a-card :title="menuItem[0]" :bordered="false">
        <Articles :PaperUrl="menuItem[1]" />
    </a-card> -->
        <div>
          <Articles :pageTitle="menuItem[0]" :PaperUrl="menuItem[1]" />
        </div>
      </a-tab-pane>
    </a-tabs>
  </section>
</template>
<script lang="ts">
import { RouterLink, RouterView } from "vue-router";
import { ref } from "vue";
import type { TabsProps } from "ant-design-vue";
import { defineComponent } from "vue";
import Articles from "./articles.vue";

export default defineComponent({
  data: () => ({
    menuItems: [],
    isLoading: false,
  }),
  methods: {
    async getAnswer() {
      // try {
      //   const res = await fetch('newspaper-sources.json')
      //   console.log((await res.json()).details)
      //    this.menuItems = (await res.json()).details
      //   console.log(this.menuItems + "what is here")
      //   //return this.menuItems.push((await res.json()).details)
      // } catch (error) {
      //   this.answer = 'Error! Could not reach the API. ' + error
      // }
      this.isLoading = true;
      fetch("newspaper-sources.json")
        .then((response) => response.json())
        .then((res) => {
          this.menuItems = res.details;
          this.isLoading = false;
        });
    },
  },
  mounted() {
    this.getAnswer();
    console.log(`the component is now mounted.`);
  },
});
</script>

<style scoped></style>
