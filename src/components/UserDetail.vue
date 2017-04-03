<template>
  <div class="component">
    <h3>You may view the User Details here</h3>
    <p>Many Details</p>
    <p>User Name: {{ switchName() }}</p>
    <!-- reset name using Custom Event -->
    <button @click="resetName()">Reset</button>

    <!-- Below is anothor way of resetting name by call-back func to Parent (without Custom Event) -->
    <button @click="resetFn()">Reset</button>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      // required: true,
      default: 'Max',
    },
    resetFn: Function,
  },
  methods: {
    switchName() {
      return this.name.split('').reverse().join('');
    },
    resetName() {
      this.name = 'Max';
      this.$emit('nameWasReset', this.name)
    },
  },
};
</script>

<style scoped>
div {
  background-color: lightcoral;
}
</style>
