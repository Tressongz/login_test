<template>
  <div>
    <button class="btn">
      <slot></slot>
    </button>
  </div>
</template>

<script>
export default {
  name: 'loginButton'
}
</script>

<script setup>

</script>

<style scoped lang="sass">
.btn
  width: 100%
  background-color: #373653
  padding: 8px
  border-radius: 4px
  color: #fff
  margin-bottom: 20px
  cursor: pointer
  transition: .5s
  &:hover
     background-color: #373653
</style>