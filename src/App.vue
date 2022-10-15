<template>
  <div class="layout">
    <!-- <a-layout-sider
      theme="light"
      collapsed-width="0"
      breakpoint="md"
      v-model:collapsed="collapsed"
      :trigger="null"
      collapsible
    >
      <NavMenu :selectedKeys="selectedKeys" />
    </a-layout-sider> -->
    <!-- <a-layout> -->
    <a-layout-header class="newscaster-header header">
      <div class="logo"><a href="/">Newscaster</a></div>
      <div class="newscaster-header-items">
        <a-button type="primary" @click="showDrawer">
          <MenuUnfoldOutlined v-if="collapsed" />
          <MenuFoldOutlined v-else />
        </a-button>
      </div>
    </a-layout-header>

    <a-layout-content>
      <div class="about">
        <!-- <a-button type="primary" @click="showDrawer">Open</a-button> -->
        <a-drawer v-model:visible="visible" class="custom-class" style="color: red" title="Menu" placement="right"
          @after-visible-change="afterVisibleChange">
          <a-menu theme="light" mode="inline">
            <RouterLink to="/">
              <a-menu-item key="1">
                <!-- <user-outlined /> -->
                <span class="news-link">Latest News</span>
              </a-menu-item>
            </RouterLink>
            <!-- <RouterLink to="/news">
              <a-menu-item key="2">
                <video-camera-outlined />
                <span>News</span>
              </a-menu-item>
            </RouterLink> -->
            <RouterLink to="/about">
              <a-menu-item key="3">
                <!-- <upload-outlined /> -->
                <span class="news-link">About</span>
              </a-menu-item>
            </RouterLink>
          </a-menu>
        </a-drawer>
      </div>
      <RouterView />
    </a-layout-content>
    <a-layout-footer style="text-align: center">
      Copyright © Newscaster {{ Date() }}
    </a-layout-footer>
    <!-- <a-layout-footer style="text-align: center">
      Ant Design ©2018 Created by Ant UED
    </a-layout-footer> -->
    <!-- </a-layout> -->
  </div>
</template>
<!-- <script lang="ts">
import {
  UserOutlined,
  VideoCameraOutlined,
  UploadOutlined,
  MenuUnfoldOutlined,
  MenuFoldOutlined,
} from "@ant-design/icons-vue";
import { defineComponent, ref } from "vue";
import { RouterLink, RouterView } from "vue-router";
import NewsToolbar from "./components/NewsToolbar.vue";
import NavMenu from "./components/NavMenu.vue";

export default defineComponent({
  components: {
    UserOutlined,
    VideoCameraOutlined,
    UploadOutlined,
    MenuUnfoldOutlined,
    MenuFoldOutlined,
  },
  setup() {
    return {
      selectedKeys: ref<string[]>(["1"]),
      collapsed: ref<boolean>(false),
      //visible: ref<boolean>(false),
    };
  },
});
</script> -->

<script lang="ts">
import { defineComponent, ref } from "vue";
import {
  UserOutlined,
  VideoCameraOutlined,
  UploadOutlined,
  MenuUnfoldOutlined,
  MenuFoldOutlined,
} from "@ant-design/icons-vue";
export default defineComponent({
  components: {
    UserOutlined,
    VideoCameraOutlined,
    UploadOutlined,
    MenuUnfoldOutlined,
    MenuFoldOutlined,
  },
  setup() {
    const visible = ref<boolean>(false);

    const afterVisibleChange = (bool: boolean) => {
      console.log("visible", bool);
    };

    const showDrawer = () => {
      visible.value = true;
    };

    const selectedKeys = ref<string[]>(["1"]);
    const collapsed = ref<boolean>(false);

    return {
      visible,
      afterVisibleChange,
      showDrawer,
      selectedKeys,
      collapsed,
    };
  },
});
</script>
<style>
.layout {
  background-color: #fff;
}

.news-link {
  font-weight: 700;
}

#components-layout-demo-custom-trigger .trigger {
  font-size: 18px;
  line-height: 64px;
  padding: 0 24px;
  cursor: pointer;
  transition: color 0.3s;
}

.logo a {
  font-size: 20px;
  font-weight: 700;
  color: #fff;
}

#components-layout-demo-custom-trigger .trigger:hover {
  color: #1890ff;
}

#components-layout-demo-custom-trigger .logo {
  height: 32px;
  background: rgba(255, 255, 255, 0.3);
  margin: 16px;
}

.site-layout .site-layout-background {
  background: #fff;
}

/* .ant-layout,
.layout {
  width: 100vw;
  height: 100%;
} */

.newscaster-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.newscaster-header-items {
  display: flex;
  align-items: center;
}

.ant-layout-content {
  margin: 0px 16px 24px 16px !important;
  padding: 0px 24px 24px 24px !important;
  min-height: 75vh;
  background: #fff;
}

.ant-tabs-tab-btn {
  font-weight: 700 !important;
}
</style>
