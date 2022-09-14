<template>
  <div class="about">
    <a-button type="primary" @click="showDrawer">Open</a-button>
    <a-drawer
      v-model:visible="visible"
      class="custom-class"
      style="color: red"
      title="Basic Drawer"
      placement="right"
      @after-visible-change="afterVisibleChange"
    >
      <a-menu selectedKeys="selectedKeys" theme="light" mode="inline">
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
        <RouterLink to="/about">
          <a-menu-item key="3">
            <upload-outlined />
            <span>About</span>
          </a-menu-item>
        </RouterLink>
      </a-menu>
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
import { defineComponent, ref } from "vue";
export default defineComponent({
  setup() {
    const visible = ref<boolean>(false);

    const afterVisibleChange = (bool: boolean) => {
      console.log("visible", bool);
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
