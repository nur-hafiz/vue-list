<template>
  <div id="app">
    <app-toggler v-bind:itemTypes="itemTypes" v-on:toggleList="toggleList($event)"></app-toggler>
    <div class="content">
      <app-form v-bind:itemTypes="itemTypes" v-on:appendItem="appendItem($event)"></app-form>
      <keep-alive>
        <component v-bind:items="items" v-bind:title="listTitle" v-bind:is="currentList"></component>
      </keep-alive>
    </div>
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import Toggler from "./components/Toggler.vue";
import Weapons from "./components/List.vue";
import Armours from "./components/List.vue";

export default {
  components: {
    "app-form": Form,
    "app-toggler": Toggler,
    "app-weapons": Weapons,
    "app-armours": Armours
  },
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      itemTypes: ["Armour", "Weapon"],
      items: {
        Armour: [],
        Weapon: []
      },
      currentList: "app-weapons",
      listTitle: "Weapons"
    };
  },
  methods: {
    appendItem: function(item) {
      this.items[item.selectedType].push(item.itemName);
    },
    toggleList: function(tab) {
      this.currentList = "app-" + tab.toLowerCase();
      this.listTitle = tab;
    }
  }
};
</script>

<style lang="scss" scoped>
#app {
  margin: 0;
}

.content {
  display: flex;
}
</style>
