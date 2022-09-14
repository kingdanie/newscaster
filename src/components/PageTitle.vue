<template>
  <a-page-header
    style="border: 1px solid rgb(235, 237, 240)"
    title="`hello`"
    @back="() => null"
  ></a-page-header>
</template>

<script lang="ts">
export default {
  props: { pageTitle: String },
  data(): any {
    return {
      // counter only uses this.initialCounter as the initial value;
      // it is disconnected from future prop updates.
      //t: this.pageTitle,
    };
  },
};
</script>
