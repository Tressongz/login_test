<template>
  <div class="wrapper">
    <div class="login_form">
      <h1 class="header">Личный кабинет</h1>
      <p class="info">Вход с помощью лицевого счёта</p>
      <div class="form">
        <div class="input_label">
          <input v-model="login" type="text" id="login_number" placeholder="00000000">
          <label for="login_number">Номер лицевого счёта</label>
        </div>
        <div class="input_label">
          <input v-model="password" :type="isShowPassword ? 'text' : 'password'" id="login_password">
          <label for="login_password">Пароль</label>
          <span class="eye" @click="togglePassword"></span>
        </div>
        <login-button @click="enter">Войти</login-button>
        <div class="hints">
          <p class="remember" style="margin-bottom: 20px">Не помните лицевой счёт или пароль?</p>
          <p class="login_phone">Вход по телефону</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref} from "vue";

const login = ref('')
const password = ref('')
const emit = defineEmits(['next'])
const isShowPassword = ref(false)

function enter() {
  if (login.value && password.value) {
      emit('next')
  }
}

function togglePassword() {
  isShowPassword.value = !isShowPassword.value
}

</script>

<style scoped lang="sass">
.eye
  position: absolute
  right: 14px
  top: 50%
  transform: translateY(-50%)
  display: inline-block
  background-image: url('@/assets/eye.svg')
  background-repeat: no-repeat
  background-size: contain
  width: 12px
  height: 12px
  cursor: pointer
  transition: .5s
  &:hover
    filter: brightness(60%)
</style>