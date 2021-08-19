<template>
  <div>
    <h1>{{message}}</h1>
    <hr>
  </div>
</template>

<script>
export default {
  //es6のメソッド記法
  data() {
    return {
      message: 'Hello Vue',
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