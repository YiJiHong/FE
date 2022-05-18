<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-teal">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          color="white"
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <img src="../assets/logo_white.png" />

        <darkmode-toggle />
        <div class="q-pa-md q-gutter-sm">
          <q-btn
            split
            class="glossy"
            color="white"
            text-color="black"
            label="LOG IN"
            to="Login"
          />

          <q-btn
            color="white"
            text-color="black"
            label="회원가입"
            to="/Signup"
          />
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer class="bg-grey-3" v-model="leftDrawerOpen">
      <q-list>
        <q-item-label header> </q-item-label>

        <SidebarMenu
          v-for="link in sidebarMenus"
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
import SidebarMenu from 'components/SidebarMenu.vue';
import DarkmodeToggle from 'src/components/DarkmodeToggle.vue';
// import SignupPage from 'pages/SignUp.vue';

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
  name: 'MainPage',

  components: {
    SidebarMenu,
    DarkmodeToggle,
  },
  // methods: {
  //   SignupPage() {},
  // },
  setup() {
    {
      const leftDrawerOpen = ref(false);

      return {
        sidebarMenus: linksList,
        text: ref(''),
        leftDrawerOpen,
        toggleLeftDrawer() {
          leftDrawerOpen.value = !leftDrawerOpen.value;
        },
        // SignupPage() {
        //   window.location.href = '../pages/SignUp.vue';
        // },
      };
    }
  },
});
</script>
