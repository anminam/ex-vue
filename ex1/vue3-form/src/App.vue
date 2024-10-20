<template>
  <form action="" @:submit.prevent="submitForm">
    <div>
      <label for="userId"></label>
      <input id="userId" type="text" v-model="username">
    </div>
    <div>
      <label for="password"></label>
      <input id="password" type="text" v-model="password">
    </div>
    <button type="submit">로그인</button>
  </form>
</template>

<script>
import axios from 'axios'
import { ref } from 'vue';

export default {
  setup() {
    const username = ref('')
    const password = ref('')

    const submitForm = () => {
      axios.post('https://jsonplaceholder.typicode.com/users', {
        username: username.value,
        password: password.value
      })
      .then(response => {
        console.log(response);
      })
    }

    return {
      username,
      password,
      submitForm
    }
  },
  methods: {
    logText() {

    }
  }
}

  // export default {
  //  data() {
  //   return {
  //     userName: '',
  //     password: ''
  //   }
  //  } ,
  //  methods: {
  //   submitForm() {
  //     const data = {
  //       username: this.userName,
  //       password:this.password
  //     }
  //     axios.post('https://jsonplaceholder.typicode.com/users', data)
  //       .then(response => {
  //         console.log(response);
  //       })
  //     console.log(this.userName, this.password);
  //     // event.preventDefault();
  //   }
  //  }
  // }
</script>

<style lang="scss" scoped>

</style>