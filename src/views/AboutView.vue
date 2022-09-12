<template>
  <div class="about">
    <h1>This is an about page</h1>
    <a-button type="primary" @click="showDrawer">Open</a-button>
  <a-drawer
    v-model:visible="visible"
    class="custom-class"
    style="color: red"
    title="Basic Drawer"
    placement="right"
    @after-visible-change="afterVisibleChange"
  >
    <p>Some contents...</p>
    <p>Some contents...</p>
    <p>Some contents...</p>
  </a-drawer>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 250px;
    display: flex;
    align-items: center;
  }
}
</style>
<script lang="ts">
  import { defineComponent, ref } from 'vue';
  export default defineComponent({
    setup() {
      const visible = ref<boolean>(false);
  
      const afterVisibleChange = (bool: boolean) => {
        console.log('visible', bool);
      };
  
      const showDrawer = () => {
        visible.value = true;
      };
  
      return {
        visible,
        afterVisibleChange,
        showDrawer,
      };
    },
  });
  </script>
  