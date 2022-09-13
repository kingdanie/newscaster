<template>
    <div>
      <a-modal
        title="title"
        :visible="showModal"
        width="100%"
      @ok="$emit('update:showModal', $event.target.value)"
      >
        <h2 v-html="title"></h2>
        <p v-html="article"></p>
      </a-modal>
    </div>
  </template>
  <script lang="ts">
  import { ref, defineComponent } from 'vue';
  export default defineComponent({
    props: {
        tile: String,
        article: String,
        showModal: Boolean
    },
    emits: ['update:showModal'],
    setup() {
      //const modalText = ref<string>('Content of the modal');
      const visible = ref<boolean>(false);  
    
      return {
        visible,
        
      };
    },

  });
  </script>
  
  