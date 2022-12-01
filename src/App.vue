<template>
  <div>
     <PageHeader />
     <PageMain />
  </div>
</template>

<script>
import PageHeader from '@/components/PageHeader.vue';
import PageMain from '@/components/PageMain.vue';

export default {
  components: {
    PageHeader,
    PageMain,
  },
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap";

   * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
</style>
