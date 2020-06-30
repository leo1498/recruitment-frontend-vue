<template>
  <div class="example-counter">
    <div class="example-counter__container">
      <div class="example-counter__counter">{{ clicks }}</div>
      <div class="example-counter__buttons">
        <button
          class="example-counter__button example-counter__increment"
          @click="increment"
        >
          +
        </button>
        <button
          class="example-counter__button example-counter__decrement"
          @click="decrement"
        >
          -
        </button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "ChimeraTpl",
  props: ["initialValue"],
  data() {
    return {
      counter: this.initialValue,
    };
  },
  computed: {
    clicks() {
      return `Current count is: ${this.counter}`;
    },
  },
  methods: {
    increment() {
      this.counter++;
      this.$emit("counterChanged", {
        type: "increment",
      });
    },
    decrement() {
      this.counter--;
      this.$emit("counterChanged", {
        type: "decrement",
      });
    },
  },
};
</script>
<style lang="scss" scoped>
.example-counter {
  &__container {
    width: 50%;
    margin: 0 auto;
    background-color: rgb(247, 247, 247);
    padding: 20px;
  }

  &__image {
    width: 100%;
    height: auto;
  }

  &__counter {
    font-size: 24px;
    text-transform: uppercase;
  }

  &__buttons {
    width: 100%;
    margin-top: 20px;
    display: flex;
  }

  &__button {
    width: 100%;
    display: block;
    border: none;
    color: #fff;
    padding: 10px;
    font-size: 20px;
    outline: none;
    cursor: pointer;
  }

  &__increment {
    background-color: green;
    margin-right: 10px;
  }

  &__decrement {
    background-color: red;
    margin-left: 10px;
  }
}
</style>
