<template>
  <div class="wrapper">
    <div class="login_form">
      <h1 class="header" style="color: #919BA6">Номер телефона</h1>
      <p class="info" style="color: #919BA6">{{ props.phone }}</p>
      <h1 class="header">Потверждение номера</h1>
      <p class="info">Мы отправили код на ваш номер<br>Введите его для подтверждения</p>
      <div class="form">
        <div class="input_label">
          <input
              @input ="changeInput(item)"
              v-for="(item, i) in 5"
              type="text"
              v-model="codeSMS[i]"
              id="login_number"
              :key="item"
              maxlength="1"
              placeholder="0"
              ref="inputCode"
          >
        </div>
        <div class="hints">
          <div class="remember" v-if="timer > 0" style="margin-bottom: 20px">Не пришло SMS? повторная отправка возможна через
            <div style="color: #00D622; display: inline-block">{{ timer }} сек</div>
          </div>
          <p class="remember" @click="sendSMS" v-else style="text-decoration: underline; margin-bottom: 24px">Отправить SMS повторно</p>
        </div>
        <login-button ref="btnContinue">Продолжить</login-button>
      </div>
    </div>
  </div>
</template>

<script setup>
import {onMounted, ref} from "vue";

const props = defineProps({
  phone: String
})

const time = 30

const inputCode = ref([])
const btnContinue = ref(null)
const timer = ref(time)
const codeSMS = ref([])

onMounted(() => {
  inputCode.value[0].focus()
  setInterval(() => {
      timer.value -= 1
    }, 1000)
  })

function changeInput(item) {
  if (item === 5) {
    btnContinue.value.$el.focus()
  } else {
    inputCode.value[item]?.focus()
  }
}

const sendSMS = () => {
  timer.value = time
  codeSMS.value = []
}

</script>

<style scoped lang="sass">
.input_label
  display: flex
  position: relative
  flex-direction: row
  justify-content: space-between
  input
    margin-bottom: 24px
    padding: 10px
    width: 39px
    height: 56px
    border-radius: 5px
    border: 1px solid #919BA6
    background-color: transparent
    font-size: 24px
  label
    position: absolute
    margin: 0 5px
    left: 0
    top: 50%
    transform: translateY(-50%)
    z-index: -1
    background-color: #fff
    padding: 0 2px
    color: #aaa
    transition: .2s
.hints
  text-decoration: none
</style>