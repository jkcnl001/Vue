<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <div id="counter">Counter: {{ counter }}</div>
  </div>
  <div id="bind-attribute">
    <span v-bind:title="message">
      Hover your mouse over me for a few seconds to see my dynamically bound
      title!
    </span>
  </div>
  <div id="event-handling">
    <p>{{ message }}</p>
    <button v-on:click="reverseMessage">Reverse Message</button>
  </div>
  <div id="two-way-binding">
    <p>{{ message }}</p>
    <input v-model="message" />
  </div>
  <div id="conditional-rendering">
    <span v-if="seen">Now you see me</span>
  </div>
  <div id="todo-list-app">
    <ol>
      <li v-for="item in groceryList" v-bind:todo="item" v-bind:key="item.id">{{ item.text}}</li>
    </ol>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data() {
    return {
      counter: 0,
      message: "You loaded this page on " + new Date().toLocaleString(),
      seen: true,
      groceryList: [
        { id: 0, text: 'Vegetables' },
        { id: 1, text: 'Cheese' },
        { id: 2, text: 'Whatever else humans are supposed to eat' }
      ]
    };
  },
  mounted() {
    setInterval(() => {
      this.counter++;
      this.seen = !this.seen;
    }, 1000);
  },
  methods: {
    reverseMessage() {
      this.message = this.message.split("").reverse().join("");
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
