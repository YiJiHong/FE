<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="bg-white">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          color="black"
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          <q-img src="~/assets/logo_black.jpg" width="672px" height="242px" />
        </q-toolbar-title>

        <darkmode-toggle />

        <div class="q-pa-md q-gutter-sm">
          <q-btn-dropdown
            split
            class="glossy"
            color="teal"
            text-color="white"
            label="LOG IN"
          >
            <q-list>
              <q-item clickable>
                <q-item-section>
                  <q-input v-model="text" label="ID" />
                </q-item-section>
                <q-item-section side> </q-item-section>
              </q-item>

              <q-item clickable>
                <q-item-section>
                  <q-input v-model="text" label="PASSWORD" />
                </q-item-section>
                <q-item-section side> </q-item-section>
              </q-item>
            </q-list>
          </q-btn-dropdown>

          <q-btn color="teal" text-color="white" label="회원가입" />
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import EssentialLink from 'components/EssentialLink.vue';
import DarkmodeToggle from 'src/components/DarkmodeToggle.vue';

const linksList = [
  {
    title: '일상',
    caption: '당신의 일상을 공유해주세요!',
    icon: 'light_mode',
    // link: 'https://quasar.dev',
  },
  {
    title: '시사/경제',
    caption: '요즘 관심가는 이슈를 들려주세요.',
    icon: 'article',
    // link: 'https://github.com/quasarframework',
  },
  {
    title: 'IT 트렌드',
    caption: 'BE, FE, QA 등등 IT가 대세래요!',
    icon: 'terminal',
    // link: 'https://chat.quasar.dev',
  },
  {
    title: '취미 생활',
    caption: '하고 나면 기쁜 일이 있으신가요?',
    icon: 'local_florist',
    // link: 'https://forum.quasar.dev',
  },
  {
    title: '운동/건강',
    caption: '당신이 오래오래 살기 위해 하는 것은?',
    icon: 'sports_basketball',
    // link: 'https://twitter.quasar.dev',
  },
  {
    title: '사랑/이별',
    caption: '기쁨, 행복, 슬픔 등 모두 알려주세요!',
    icon: 'favorite',
    // link: 'https://facebook.quasar.dev',
  },
  {
    title: '지식',
    caption: '사소한 지식도 좋아요, 공유해주세요!',
    icon: 'menu_book',
    // link: 'https://awesome.quasar.dev',
  },
];

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink,
    DarkmodeToggle,
  },

  setup() {
    {
      const leftDrawerOpen = ref(false);

      return {
        essentialLinks: linksList,
        text: ref(''),
        leftDrawerOpen,
        toggleLeftDrawer() {
          leftDrawerOpen.value = !leftDrawerOpen.value;
        },
      };
    }
  },
});
</script>
