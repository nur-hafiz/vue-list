<template>
  <form class="main">
    <h1 class="form-header">Item adder</h1>

    <section class="form-section">
      <label>Item Name:</label>
      <input class="section-input" name="itemName" placeholder="Item Name" v-model="itemName">
    </section>

    <section class="form-section">
      <label>Item Type:</label>
      <select v-model="selectedType" class="section-input">
        <option v-for="itemType in itemTypes">{{itemType}}</option>
      </select>
    </section>

    <button v-on:click="submitItem($event)">Add Item</button>
  </form>
</template>

<script>
export default {
  props: {
    itemTypes: {
      type: Array
    }
  },
  data() {
    return {
      itemName: "",
      selectedType: ""
    };
  },
  methods: {
    submitItem: function() {
      event.preventDefault();
      this.$emit("appendItem", {
        itemName: this.itemName,
        selectedType: this.selectedType
      });
    }
  }
};
</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.main {
  flex: 1;
  padding-bottom: 10px;
  border: 2px solid black;
  border-top: none;
}

.main > * {
  margin-left: 10px;
}

.form-header {
  margin-bottom: 20px;
}

.form-section {
  margin-bottom: 10px;

  display: flex;
  flex-direction: column;
}
.section-input {
  width: 70%;
  height: 25px;
  margin-top: 5px;
  padding-left: 5px;
}
</style>

