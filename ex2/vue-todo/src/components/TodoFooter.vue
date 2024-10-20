<template>
  <div class="clearAllContainer">
    <span class="btn" @click="remove">clear All</span>
  </div>
</template>

<script>
export default {
  methods: {
    remove() {
      localStorage.clear();
    },
  },
};
</script>

<style lang="scss" scoped>
.clearAllContainer {
  width: 8rem;
  height: 50px;
  line-height: 50px;
  background: white;
  border-radius: 5px;
  margin: 0 auto;
}

.btn {
  color: #e20303;
  display: block;
}
</style>
