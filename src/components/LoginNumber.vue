<template>
  <div class="wrapper">
    <div class="login_form">
      <h1 class="header">Введите номер телефона</h1>
      <p class="info" style="text-align: justify">В целях безопасности мы переводим всех абонентов Данцер на авторизацию с помощью номера телефона. В дальнейшем вы можете использовать его для входа</p>
      <div class="form">
        <div class="input_label">
          <input v-model="phone" type="text" id="login_number" placeholder="+7">
          <label for="login_number">Номер телефона</label>
        </div>
        <login-button @click="enter">Продолжить</login-button>
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref} from "vue";

const phone = ref('')
const emit = defineEmits(['next'])

function enter() {
  if (phone.value) {
    emit('next', phone.value)
  }
}
</script>

<style scoped lang="sass">

</style>