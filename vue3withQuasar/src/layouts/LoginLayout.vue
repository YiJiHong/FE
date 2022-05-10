<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-teal">
      <q-toolbar>
        <q-toolbar-title> ONEGO </q-toolbar-title> <darkmode-toggle
      /></q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import DarkmodeToggle from 'src/components/DarkmodeToggle.vue';

export default defineComponent({
  name: 'LoginLayout',

  components: {
    DarkmodeToggle,
  },

  setup() {
    {
      return {};
    }
  },
});
</script>
