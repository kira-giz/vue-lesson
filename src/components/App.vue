<template>
  <div>
    <h1>{{message}}</h1>
    <hr>
    <ChildComponent></ChildComponent>
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
    }
  }
}
</script>

<style scoped>
  h1 {
    color: green;
  }

  hr {
    margin: 16px 0;
  }
</style>