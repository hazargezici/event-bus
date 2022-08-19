<template>
  <div>
    <AddTag @sendTag="alert($event.target.value)" />
  </div>
</template>

<script>
import AddTag from "./components/AddTag.vue";
export default {
  data: function () {
    return {
      tag: "",
    };
  },
  components: { AddTag },
  // created() {
  //   EventBus.$on("sendTag", (data) => {
  //     this.tag = data;
  //     alert(this.tag);
  //   });
  // },
};
</script>

<style>
body {
  color: #9ab7ef;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
