<template>
  <div ref="switchRef" @click="switchEvent">
    <div v-if="darkMode">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="25"
        height="25"
        viewBox="0 0 25 25"
        fill="currentColor"
        class="bi bi-moon-stars-fill none:event"
      >
        <path
          d="M6 .278a.768.768 0 0 1 .08.858a7.208 7.208 0 0 0-.878 3.46c0 4.021 3.278 7.277 7.318 7.277c.527 0 1.04-.055 1.533-.16a.787.787 0 0 1 .81.316a.733.733 0 0 1-.031.893A8.349 8.349 0 0 1 8.344 16C3.734 16 0 12.286 0 7.71C0 4.266 2.114 1.312 5.124.06A.752.752 0 0 1 6 .278z"
        />
        <path
          d="M10.794 3.148a.217.217 0 0 1 .412 0l.387 1.162c.173.518.579.924 1.097 1.097l1.162.387a.217.217 0 0 1 0 .412l-1.162.387a1.734 1.734 0 0 0-1.097 1.097l-.387 1.162a.217.217 0 0 1-.412 0l-.387-1.162A1.734 1.734 0 0 0 9.31 6.593l-1.162-.387a.217.217 0 0 1 0-.412l1.162-.387a1.734 1.734 0 0 0 1.097-1.097l.387-1.162zM13.863.099a.145.145 0 0 1 .274 0l.258.774c.115.346.386.617.732.732l.774.258a.145.145 0 0 1 0 .274l-.774.258a1.156 1.156 0 0 0-.732.732l-.258.774a.145.145 0 0 1-.274 0l-.258-.774a1.156 1.156 0 0 0-.732-.732l-.774-.258a.145.145 0 0 1 0-.274l.774-.258c.346-.115.617-.386.732-.732L13.863.1z"
        />
      </svg>
    </div>

    <div v-else>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="25"
        height="25"
        viewBox="0 0 25 25"
        fill="currentColor"
      >
        <path
          d="M12 6a1 1 0 0 0 1-1V3a1 1 0 0 0-2 0v2a1 1 0 0 0 1 1Zm9 5h-2a1 1 0 0 0 0 2h2a1 1 0 0 0 0-2ZM6 12a1 1 0 0 0-1-1H3a1 1 0 0 0 0 2h2a1 1 0 0 0 1-1Zm.22-7a1 1 0 0 0-1.39 1.47l1.44 1.39a1 1 0 0 0 .73.28a1 1 0 0 0 .72-.31a1 1 0 0 0 0-1.41ZM17 8.14a1 1 0 0 0 .69-.28l1.44-1.39A1 1 0 0 0 17.78 5l-1.44 1.42a1 1 0 0 0 0 1.41a1 1 0 0 0 .66.31ZM12 18a1 1 0 0 0-1 1v2a1 1 0 0 0 2 0v-2a1 1 0 0 0-1-1Zm5.73-1.86a1 1 0 0 0-1.39 1.44L17.78 19a1 1 0 0 0 .69.28a1 1 0 0 0 .72-.3a1 1 0 0 0 0-1.42Zm-11.46 0l-1.44 1.39a1 1 0 0 0 0 1.42a1 1 0 0 0 .72.3a1 1 0 0 0 .67-.25l1.44-1.39a1 1 0 0 0-1.39-1.44ZM12 8a4 4 0 1 0 4 4a4 4 0 0 0-4-4Z"
        />
      </svg>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref, nextTick } from 'vue';

export default defineComponent({
  name: 'DarkmodeToggle',

  setup() {
    const darkMode = ref<boolean>(false);
    const switchRef = ref<unknown>(null);
    const switchMode = ref<boolean>(false);

    if (
      localStorage.getItem('preferedDarkMode') &&
      localStorage.getItem('prefferedDarkMode') === 'true'
    ) {
      nextTick(() => {
        switchMode.value = true;
        switchToggle();
      });
    } else {
    }
    if (
      window.matchMedia &&
      window.matchMedia('(prefers-color-schema: dark)').matches
    ) {
      nextTick(() => {
        switchMode.value = true;
        switchToggle();
      });
    }
    const darkAttrs = () => {
      if (darkMode.value) {
        document.documentElement.setAttribute('data-mode', 'dark');
        document.body.classList.add('darker');
        localStorage.setItem('prefferedDarkMode', 'true');
      } else {
        document.documentElement.removeAttribute('data-mode');
        localStorage.setItem('prefferedDarkMode', 'false');
      }
    };

    const switchToggle = () => {
      if (switchMode.value) {
        darkMode.value = true;
        darkAttrs();
        switchMode.value = false;
      } else {
        darkMode.value = false;
        darkAttrs();
        switchMode.value = true;
      }
    };

    const switchEvent = () => {
      nextTick(() => {
        switchToggle();
      });
    };
    return {
      switchRef,
      switchEvent,
      darkMode,
    };
  },
});
</script>

<style scoped>
@media (prefers-color-scheme: dark) {
  [data-mode='dark'].darker {
    color: var(--alga-white);
    background-color: var(--alga-darker);
    border-color: var(--alga-darker);
  }
}
</style>

<!-- <template>
  <q-toggle
    v-model="darkMode"
    checked-icon="check"
    color="teal"
    unchecked-icon="clear"
    keep-color
  />
</template>
<script lang="ts">
import { defineComponent, ref, watch, onMounted } from 'vue';
import { useQuasar } from 'quasar';

export default defineComponent({
  name: 'DarkmodeToggle',

  setup() {
    const darkMode = ref(false);
    const $q = useQuasar();

    watch(darkMode, (darkMode) => {
      $q.dark.set(darkMode);
      $q.localStorage.set('darkMode', darkMode);
    });

    watch(
      () => $q.dark.isActive,
      (val) => {
        console.log(val ? 'On dark mode' : 'On light mode');
      }
    );

    onMounted(() => {
      const darkModeIsActive = $q.localStorage.getItem('darkMode');
      if (darkModeIsActive) {
        darkMode.value = true;
      }
    });
    return {
      darkMode,
    };
  },
});
</script> -->
