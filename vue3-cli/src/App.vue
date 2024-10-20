<template>
  <AppHeader :title="title"/>
  <ChangeButton @change="changeTitle" />
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import ChangeButton from './components/ChangeButton.vue';

  export default {
    data() {
      return {
        title: '바보야g'
      }
    },
    components: {
      AppHeader,
      ChangeButton
    },
    methods: {
      changeTitle() {
        this.title = '바뀐거'
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>