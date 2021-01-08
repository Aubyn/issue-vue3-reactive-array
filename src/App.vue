<script setup>
import VueNext from './components/VueNext.vue';

import { ref, reactive, provide, watchEffect } from 'vue';

const cars = ['car1', 'car2'],
  pens = reactive(['pen1', 'pen2']);
provide('cars', cars);
provide('pens', pens);

/* const { receivedData, receiveHandler } = {
  receivedData: reactive([]),
  receiveHandler: function (arg1, arg2) {
    receivedData.push([arg1, arg2]);
  }
}; */
const receivedData = reactive([]);
const receiveHandler = function (arg1, arg2) {
  receivedData.push([arg1, arg2]);
  console.log(receivedData)
  // receivedData.splice(0, receivedData.length, arg1, arg2);
};

watchEffect(() => {
  console.log(receivedData);
});
</script>

<template>
  <vue-next @receive="receiveHandler">
    <template v-slot:default>
      <p
        class="text-gray-500"
      >Lorem ipsum dolor sit amet consectetur, adipisicing elit. Modi, accusantium!</p>
      <p>provide/inject: {{ pens }}</p>
      <p>emit in slot: {{ receivedData }}</p>
    </template>
    <template v-slot:name>
      <h3>Hello, Vue3!</h3>
    </template>
  </vue-next>
</template>

<style>
</style>