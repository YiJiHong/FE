<!--원본-->
<template>
  <q-page padding>
    <q-form class="row justify-center" @submit.prevent="">
      <!--제목-->
      <p class="col-12 text-h4 text-center q-padding-lg">Login</p>
      <!--로그인 입력 부분-->
      <div class="input-wrap">
        <div class="col-md-4 col-sm-6 col-xs-10 q-gutter-y-lg">
          <q-input label="ID" v-model="form.id" />
          <q-input label="Password" type="password" v-model="form.password" />
        </div>
      </div>
      <!--로그인 버튼 구현-->
      <div class="full-width q-pt-md" align="center">
        <q-btn
          outline
          rounded
          class="q-mt-lg"
          color="teal"
          label="Login"
          size="lg"
        />
      </div>

      <div class="full-width" align="center">
        <q-btn
          rounded
          class="q-mt-lg"
          text-color="teal"
          flat
          color="teal-1"
          label="회원가입"
          size="lg"
          to="/Signup"
        />
      </div>
    </q-form>
  </q-page>
</template>
<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'PageLogin',

  setup() {
    const form = ref({ id: '', password: '' });

    return {
      form,
    };
  },
});
</script>
