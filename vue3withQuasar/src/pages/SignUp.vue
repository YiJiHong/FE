<!--시작-->
<template>
  <q-page padding>
    <q-form class="row justify-center" @submit.prevent="">
      <!--제목-->
      <p class="col-12 text-h4 text-center q-padding-lg">Sign Up</p>
      <!--sign up 입력 박스 구현-->
      <div class="input-wrap">
        <div class="col-md-4 col-sm-6 col-xs-10 q-gutter-y-lg">
          <q-input
            filled
            color="teal"
            label="이름"
            v-model="form.name"
            class="q-mt-lg"
          />
          <q-input
            filled
            color="teal"
            label="이메일"
            v-model="form.email"
            class="q-mt-lg"
          />
          <q-input
            filled
            color="teal"
            label="닉네임"
            v-model="form.nickname"
            class="q-mt-lg"
          />
          <q-input
            filled
            color="teal"
            label="비밀번호"
            type="password"
            v-model="form.password"
            class="q-mt-lg"
          />
          <q-input
            label="비밀번호 확인"
            v-model="form.checkpassword"
            filled
            :type="isPwd ? 'password' : 'text'"
            hint="Password with toggle"
            class="q-mt-lg"
          >
            <template v-slot:append>
              <q-icon
                :name="isPwd ? 'visibility_off' : 'visibility'"
                class="cursor-pointer"
                @click="isPwd = !isPwd"
              ></q-icon>
            </template>
          </q-input>
        </div>
        <!--submit 버튼 구현-->
        <div class="full-width q-pt-md" align="center">
          <q-btn
            outline
            rounded
            class="q-mt-lg"
            color="teal"
            label="Submit"
            size="lg"
          />
        </div>
      </div>
    </q-form>
  </q-page>
</template>
<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'PageSignUp',

  setup() {
    const form = ref({
      name: '',
      email: '',
      nickname: '',
      password: '',
      checkpassword: '',
    });

    return {
      form,
      isPwd: ref(true),
    };
  },
});
</script>
