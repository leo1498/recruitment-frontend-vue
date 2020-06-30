<template>
  <div>
    <ExampleCounter :initialValue="3" @counterChanged="handleCounterChanged"></ExampleCounter>
    <div>{{ childEvent }}</div>
  </div>
</template>
<script>
import ExampleCounter from "./../src/ExampleCounter";

export default {
  name: "ExampleCounterSandbox",
  components: { ExampleCounter },
  data() {
    return {
      childEvent: ""
    }
  },
  methods: {
    handleCounterChanged(payload) {
      this.childEvent = "Action: " + payload.type;
    }
  }
};
</script>
<style lang="scss" scoped></style>
