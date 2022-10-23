
TS
<template>
    <!-- <a-alert
    message="Warning Text Warning Text Warning TextW arning Text Warning Text Warning TextWarning Text"
    type="warning"
    closable
    @close="onClose"
  /> -->
    <a-alert message="An error occurred" description="Sorry, we are unable to get news articles from this category at this time, please visit other categories." type="error"
        closable @close="onClose" />
</template>
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    setup() {
        const onClose = (e: MouseEvent) => {
            //return window.location.replace("/");
            return location.assign('/')
        };
        return {
            onClose,
        };
    },
});
</script>