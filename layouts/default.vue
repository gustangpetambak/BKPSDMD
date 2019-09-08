<template>
  <a-layout style="min-height: 100vh">
    <no-ssr>
      <a-layout-sider collapsible v-model="collapsed">
        <header-app />
      </a-layout-sider>
      <a-layout>
        <a-layout-header style="background: #fff; padding: 0" />
        <a-layout-content style="margin: 16px">
          <nuxt />
        </a-layout-content>
        <a-layout-footer style="text-align: center">
          <footer-app />
        </a-layout-footer>
      </a-layout>
    </no-ssr>
  </a-layout>
</template>
<script>
import headerApp from "~/components/header/app.vue";
import footerApp from "~/components/footer/app.vue";
export default {
  data() {
    return {
      collapsed: false
    };
  },
  components: {
    headerApp,
    footerApp
  }
};
</script>