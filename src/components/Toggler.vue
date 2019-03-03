<template>
  <section class="main">
    <div v-on:click="toggleList($event)" class="itemContainer" v-for="itemType in itemTypes">
      <h1 class="itemType">{{itemType + "s"}}</h1>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    itemTypes: {
      type: Array
    }
  },
  data() {
    return {};
  },
  methods: {
    toggleList: function(tab) {
      this.$emit("toggleList", tab.target.textContent);
    }
  }
};
</script>

<style lang="scss" scoped>
.main {
  display: flex;
  background: lightseagreen;
}

.itemContainer {
  flex: 1;
  text-align: center;
  border: 2px solid #222;
  border-left: none;

  &:hover {
    cursor: pointer;
  }

  &:first-of-type {
    border-left: 2px solid #222;
  }
}
</style>
