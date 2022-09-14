<template>
  <a-layout>
  
    <a-layout-sider theme="light" collapsed-width="0" breakpoint="md" v-model:collapsed="collapsed" :trigger="null" collapsible>
      <!-- <div class="logo" >Newscaster</div> -->
      <!-- <a-menu v-model:selectedKeys="selectedKeys" theme="dark" mode="inline">
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
      </a-menu> -->
      <NavMenu :selectedKeys="selectedKeys"/>
    </a-layout-sider>
    <a-layout>
      <a-layout-header class="newscaster-header header">
      <div class="logo" >Newscaster</div>
      <div class="newscaster-header-items">
      

      <a-button type="primary" @click="() => (collapsed = !collapsed)">
      <MenuUnfoldOutlined v-if="collapsed" />
      <MenuFoldOutlined v-else />
    </a-button>
  </div>
    </a-layout-header>
    
      <!-- <a-layout-header  style="background: #fff; padding: 0">
        <menu-unfold-outlined
          v-if="collapsed"
          class="trigger"
          @click="() => (collapsed = !collapsed)"
        />
        <menu-fold-outlined v-else class="trigger" @click="() => (collapsed = !collapsed)" />
      </a-layout-header> -->
  
      <a-layout-content
        :style="{ margin: '24px 16px', padding: '24px', background: '#fff', minHeight: '280px' }"
      >
        <RouterView />
      </a-layout-content>
      <a-layout-footer style="text-align: center">
        Newscaster {{ Date()}} Copyright
      </a-layout-footer>
    </a-layout>
  </a-layout>
</template>
<script lang="ts">
import {
  UserOutlined,
  VideoCameraOutlined,
  UploadOutlined,
  MenuUnfoldOutlined,
  MenuFoldOutlined,
} from '@ant-design/icons-vue';
import { defineComponent, ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import NewsToolbar from './components/NewsToolbar.vue'
import NavMenu from './components/NavMenu.vue'

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
      selectedKeys: ref<string[]>(['1']),
      collapsed: ref<boolean>(false),
    };
  },
});
</script>
<style>
#components-layout-demo-custom-trigger .trigger {
  font-size: 18px;
  line-height: 64px;
  padding: 0 24px;
  cursor: pointer;
  transition: color 0.3s;
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

.ant-layout{
  width: 100vw;
  height: 100%
}

.newscaster-header{
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.newscaster-header-items{
  display: flex;
  align-items: center;
}

.logo{
  color: #fff;
}
</style>
