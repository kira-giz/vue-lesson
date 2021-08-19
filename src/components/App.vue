<template>
  <div>
    <h1 v-html="message" :class="classObject"></h1>
    <hr>
    <ChildComponent v-show="isShow"></ChildComponent>
    <p v-if="id === 12">1</p>
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
    id: 12,
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