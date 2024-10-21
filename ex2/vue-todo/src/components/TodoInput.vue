<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" @keyup.enter="addTodo" />

    <span class="addContainer" @click="addTodo">
      <FontAwesomeIcon icon="fa-plus" />
    </span>
  </div>
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

export default {
  data() {
    return {
      newTodoItem: '',
    };
  },
  components: { FontAwesomeIcon },
  methods: {
    addTodo() {
      if (!this.newTodoItem) {
        return;
      }

      this.$emit('onAdd', this.newTodoItem);
      this.clearInput();
    },
    clearInput() {
      this.newTodoItem = '';
    },
  },
};
</script>

<style lang="scss" scoped>
input:focus {
  outline: none;
}

.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;

  input {
    border-style: none;
    font-size: 0.9rem;
  }
}

.addContainer {
  float: right;
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
  i {
    color: white;
    vertical-align: middle;
  }
}
</style>
