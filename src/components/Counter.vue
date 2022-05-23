<template>
  <h2>{{ customTitle }}</h2>
  <p>{{ counter }} <sup>2</sup> = {{ squareCounter }}</p>
  <div>
    <button @click="increase">+</button>
    <button @click="decrease">-</button>
  </div>
</template>

<script>
//import { number, string } from "yargs";

export default {
  props: {
    title: String,
    start: {
      type: Number,
      default: 15,
      validator(value) {
        return value >= 0;
      },
    },
  },
  //name: 'Counter',
  data() {
    return {
      counter: this.start,
    };
  },
  methods: {
    increase() {
      this.counter++;
    },
    decrease() {
      this.counter--;
    },
  },
  computed: {
    squareCounter() {
      return this.counter * this.counter;
    },
    customTitle() {
      return this.title ? this.title : "Titul predeterminat";
      // return this.title || "Titul predeterminat" -> Opció correcte igual
    },
  },
};
</script>

<style>
button {
  width: 4rem;
  font-size: 1.5em;
  padding: 0.5em;
  margin: 0.5em;
  border-radius: 3px;
  border: 1px solid #ccc;
  background: #eee;
}
button:hover {
  background: #ddd;
  transition: ease-in-out 0.3s;
}
</style>
