<template>
  <div>
    <h1>Vue 3 Counter App</h1>
    <p>Current Count: {{ count }}</p>
    <button @click="increment">Increment</button>
    <button @click="decrement">Decrement</button>
    <button @click="reset">Reset</button>

    <!-- 5. Class and Style Bindings -->
    <div :class="{ 'highlight': count % 2 === 0 }" :style="{ color: count % 2 === 0 ? 'blue' : 'red' }">
      Conditional Styling
    </div>

    <!-- 9. Watchers -->
    <p v-if="count >= 10">Count is 10 or greater</p>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  data() {
    return {
      count: ref(0),
    };
  },
  methods: {
    increment() {
      this.count++;
    },
    decrement() {
      this.count--;
    },
    reset() {
      this.count = 0;
    },
  },
  // 5. Class and Style Bindings
  computed: {
    isEven() {
      return this.count % 2 === 0;
    },
  },
};
</script>

<style>
.highlight {
  font-weight: bold;
}
</style>
