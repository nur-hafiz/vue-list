<template>
  <div class="main">
    <h1>{{title}}</h1>
    <ol class="item-list">
      <li v-for="item in itemList">{{item}}</li>
    </ol>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String
    },
    items: {}
  },
  data() {
    return {
      itemList: []
    };
  },
  created() {
    let items = this.items;
    let key = this.title.slice(0, this.title.length - 1);
    this.itemList = items[key];
  }
};
</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
}

.main {
  flex: 1;
  border: 2px solid #222;
  border-top: none;
  border-left: none;
}

.main > * {
  margin-left: 10px;
}

.item-list li {
  list-style-position: inside;
}
</style>
