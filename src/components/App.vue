<template>
  <div>
    <h1 v-html="message" :class="classObject"></h1>
    <hr>
    <ChildComponent v-show="isShow"></ChildComponent>
    <p v-if="id === 12">1</p>
    <p v-else-if="id === 2">2</p>
    <template v-else-if="id === 3">
      <p>2-1</p>
      <p>2-2</p>
      <p>2-3</p>
    </template>
    <p v-else>other</p>
  </div>
</template>

<script>
import ChildComponent from './ChildComponent';
export default {
  components: {
    ChildComponent
  },
  //es6のメソッド記法
  data() {
    return {
    message: '<span>Hello Vue</span>',
    isShow: true,
    id: 3,
    classObject: {
      'is-green': true
    }
    }
  }
}
</script>

<style scoped>
  .is-green {
    color: green;
  }
  hr {
    margin: 16px 0;
  }
</style>