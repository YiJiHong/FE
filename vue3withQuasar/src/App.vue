<template>
  <div id="header">
    <main-header />
  </div>
  <router-view />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import HeaderAndDrawerVue from './layouts/HeaderAndDrawer.vue';

// import { useQuasar } from 'quasar';

export default defineComponent({
  name: 'App',
  data() {
    return {
      mode: 'dark',
    };
  },
  components: {
    'main-header': HeaderAndDrawerVue,
  },
  // setup() {
  //   // const $q = useQuasar();
  //   // $q.dark.set(true);
  // },
});
</script>
