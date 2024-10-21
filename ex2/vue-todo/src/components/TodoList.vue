<template>
  <ul>
    <li v-for="(item, index) in items" :key="index" class="shadow">
      <span class="checkBtn" @click="complete(item)">
        <FontAwesomeIcon
          icon="fa-check"
          :class="{ checkBtnCompleted: item.completed }"
        />
      </span>
      <span :class="{ textCompleted: item.completed }">
        {{ item.item }}
      </span>
      <span class="removeBtn" @click="removeTodo(item)">
        <FontAwesomeIcon icon="fa-trash" />
      </span>
    </li>
  </ul>
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

export default {
  props: ['items'],
  components: {
    FontAwesomeIcon,
  },
  methods: {
    removeTodo(item) {
      this.$emit('onRemove', item);
    },
    complete(item) {
      this.$emit('onComplete', item);
    },
  },
};
</script>

<style lang="scss" scoped>
ul,
li {
  list-style: none;
  margin: 0;
  padding: 0;
  text-align: left;
}

li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}

.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
</style>
