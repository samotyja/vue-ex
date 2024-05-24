<template>
  <p>{{ counter }}</p>
  <button @click.prevent="click">Click me</button>
</template>

<script>
export default {
  data() {
    return {
      counter: 0,
    };
  },
  methods: {
    click() {
      this.counter++;
    },
  },
};
</script>
