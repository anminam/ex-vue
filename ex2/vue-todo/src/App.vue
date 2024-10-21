<template>
  <div>
    <TodoHeader />
    <TodoInput @onAdd="addOneItem" />
    <TodoList :items="items" @onRemove="removeItem" @onComplete="toggleItem" />
    <TodoFooter @onAllRemove="removeAll" />
  </div>
</template>

<script>
import TodoFooter from './components/TodoFooter.vue';
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';

export default {
  data() {
    return {
      items: [],
    };
  },
  created() {
    if (localStorage.length) {
      for (var i = 0; i < localStorage.length; i++) {
        const item = localStorage.getItem(localStorage.key(i));
        this.items.push(JSON.parse(item));
      }
    }
  },
  components: {
    TodoFooter,
    TodoHeader,
    TodoList,
    TodoInput,
  },
  methods: {
    addOneItem(item) {
      const obj = {
        completed: false,
        item,
      };
      // console.log(item);
      localStorage.setItem(item, JSON.stringify(obj));
      this.items.push(obj);
    },
    removeItem(item) {
      localStorage.removeItem(item.item);
      this.items = this.items.filter((i) => i.item !== item.item);
    },
    toggleItem(item) {
      item.completed = !item.completed;

      localStorage.removeItem(item.item);
      localStorage.setItem(item.item, JSON.stringify(item));
    },
    removeAll() {
      this.items = [];
      localStorage.clear();
    },
  },
};
</script>

<style lang="scss">
body {
  text-align: center;
  background: #f6f6f6;
}

input {
  border-style: groove;
  width: 200px;
}
button {
  border-style: groove;
}

.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.1);
}
</style>
