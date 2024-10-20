<template>
  <button @click="btnClick">
바꿔라
  </button>
</template>

<script>
  export default {
    methods: {
      btnClick() {
        this.$emit('change')
      }
    }
  }
</script>

<style lang="sass" scoped>

</style>