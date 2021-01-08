<script setup>
import { ref, reactive, shallowReactive, inject, defineEmit } from 'vue';

/* reactivity */
const count = ref(0);
const incCount = function () {
  count.value++;
};

const user = shallowReactive({
  name: 'user1',
  age: 0,
  list: ['tv']
});
const incAge = function () {
  user.age++;
};

/* transfer data */
const [cars, pens] = [inject('cars'), inject('pens')];
const updatePens = function () {
  pens.push('penx');
};
pens.push('pen3')

const emit = defineEmit(['receive']);
</script>

<template>
  <div id="vuenext">
    <section class="mx-8 my-8 border-2 border-solid border-gray-600">
      <header>
        <h3 class="my-2 text-gray-400 text-xl">reactivity</h3>
      </header>
      <button
        class="border border-solid border-gray-200 rounded-sm bg-green-200 px-2 py-1"
        @click="incCount"
      >Counter：{{ count }}</button>
      <button
        class="border border-solid border-gray-200 rounded-sm bg-yellow-200 px-2 py-1"
        @click="incAge"
      >Age：{{ user.age }}</button>
    </section>
    <section class="mx-8 my-8 border-2 border-solid border-gray-600">
      <header>
        <h3 class="my-2 text-gray-400 text-xl">slot</h3>
      </header>
      <slot>default</slot>
      <slot name="name">lack name</slot>
    </section>
    <section class="mx-8 my-8 border-2 border-solid border-gray-600">
      <header>
        <h3 class="my-2 text-gray-400 text-xl">transfer data</h3>
      </header>
      <p>provide/inject: {{ cars }} {{ pens }}</p>
      <button
        class="block border border-solid border-gray-200 rounded-sm bg-blue-200 px-2 py-1"
        @click="updatePens"
      >updateInject</button>
      <button
        class="block border border-solid border-gray-200 rounded-sm bg-blue-200 px-2 py-1"
        @click="$emit('receive', 'emit', 'receive')"
      >emit</button>
    </section>
  </div>
</template>

<style scoped>
</style>