<template>
  <div class="component">
    <h3>You may view the User Details here</h3>
    <p>Many Details</p>
    <p>User Name: {{ switchName() }}</p>
    <p>User Age: {{ userAge }}</p>
    <!-- reset name using Custom Event -->
    <button @click="resetName()">Reset</button>

    <!-- Below is anothor way of resetting name by call-back func to Parent (without Custom Event) -->
    <button @click="resetFn()">Reset</button>
  </div>
</template>

<script>
import { eventBus } from '../main';

export default {
  props: {
    name: {
      type: String,
      // required: true,
      default: 'Max',
    },
    resetFn: Function,
    userAge: Number,
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
  created() {
    eventBus.$on('ageWasEdited', (age) => {
      this.userAge = age;
    });
  },
};
</script>

<style scoped>
div {
  background-color: lightcoral;
}
</style>
