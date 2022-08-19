<template>
  <div class="container">
    <div class="wrapper">
      <div class="header">
        <h1>Add Item</h1>
        <input
          type="text"
          v-model="input"
          @keyup.enter="addToItems"
          placeholder="Add any item"
        />
        <button @click="addToItems"><img src="../assets/plus.png" /></button>
      </div>
      <div class="body">
        <ul>
          <li v-for="item in items" :key="item">{{ item }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import EventBus from "@/components/event-bus";
export default {
  data: function () {
    return {
      input: "",
      items: [],
    };
  },
  methods: {
    addToItems() {
      if (!this.input) {
        return;
      }
      this.items.push(this.input);
      EventBus.$emit("sendTag", this.input);
      this.input = "";
    },
  },
};
</script>
<style lang="scss" scoped>
* {
  border: 0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  background-color: #161c27;
  height: 100vh;
  display: flex;
  align-items: center;
  padding: 0 300px;
  .wrapper {
    background-color: #111620;
    width: 100%;
    border: 10px solid #344454;
    padding: 40px;
    border-radius: 20px;
    .header {
      input {
        padding: 20px 0 20px 50px;
        width: 100%;
        background-color: #161c27;
        border: 1px solid #273245;
        color: #9ab7ef;
        &:focus {
          outline: none;
        }
      }
      button {
        border: none;
        position: relative;
        top: -50px;
        left: 5px;
        padding: 10px;
        background-color: #161c27;
        img {
          width: 20px;
          background-color: #161c27;
        }
        &:hover {
          cursor: pointer;
        }
      }
    }
    .body {
      li {
        list-style: none;
        display: inline-block;
        background-color: #142037;
        border-radius: 20px;
        margin: 0 0 10px 20px;
        padding: 10px 20px;
        &:hover {
          background-color: #92b6ff;
          color: #111620;
          cursor: pointer;
        }
      }
    }
  }
}
</style>
