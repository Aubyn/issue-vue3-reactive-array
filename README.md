# issue-vue3-reactive-array

## issue state

https://github.com/vuejs/vue-next/issues/2972

`replied`: bug of `<script setup>`

## run

```
yarn
yarn dev
```

## issue

### Version

3.0.5

### Reproduction link

https://github.com/Aubyn/issue-vue3-reactive-array.git

### Steps to reproduce

0. clone, run `yarn` and `yarn dev` in terminal
1. use `assignment 2` to create reactive array, named as `receivedData` in `App.vue`
2. click `emit` button on the page
3. DOM view didn't update(`why`) as `receivedData` updated
4. use `assignment 1`
5. click `emit` button
6. DOM view updates as `receivedData` updated(`why`)

```javascript
/* assignment 1 */
const { receivedData, receiveHandler } = {
  receivedData: reactive([]),
  receiveHandler: function (arg1, arg2) {
    receivedData.push([arg1, arg2]);
  }
};
```

```javascript
/* assignment 2 */
const receivedData = reactive([]);
const receiveHandler = function (arg1, arg2) {
  receivedData.push([arg1, arg2]);
};
```

### What is expected?

`assignment 1` and `assignment 2` trigger DOM update.

### What is actually happening?

`assignment 1` did trigger DOM update, but `assignment 2` didn't.