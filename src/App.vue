<template>
  <login-form @next="state++" v-if="state === stateNames.form"/>
  <login-number @next="update" v-else-if="state === stateNames.number"/>
  <login-code  :phone = "phone" v-else-if="state === stateNames.code"/>
</template>


<script setup>
import LoginForm from './components/LoginForm.vue';
import LoginNumber from  './components/LoginNumber.vue'
import LoginCode from "./components/LoginCode.vue";
import {ref} from "vue";

const stateNames = {
  form: 1,
  number: 2,
  code: 3
}

const state = ref(stateNames.form)
const phone = ref('')

function update(ph) {
  state.value += 1
  phone.value = ph
}
</script>

<style scoped lang="sass">

</style>
