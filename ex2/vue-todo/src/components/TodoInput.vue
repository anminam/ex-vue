<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" @keyup.enter="addTodo" />

    <span class="addContainer" @click="addTodo">
      <FontAwesomeIcon icon="fa-plus" />
    </span>

    <ModalNormal v-if="isModal" @close="closeModal">
      <template #header>
        <h3>경고!</h3>
      </template>
      <template #body> 무엇이든 입력하세요 </template>
      <template #footer> copy light </template>
    </ModalNormal>
    <button id="show-modal" @click="showModal">ShowModal</button>
  </div>
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import ModalNormal from './common/ModalNormal.vue';

export default {
  data() {
    return {
      newTodoItem: '',
      isModal: false,
    };
  },
  props: { show: Boolean },
  components: { FontAwesomeIcon, ModalNormal },
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
    closeModal() {
      this.isModal = false;
    },
    showModal() {
      this.isModal = true;
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
