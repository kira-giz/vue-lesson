<template>
  <div>
    <h1 v-html="message" :class="classObject"></h1>
    <hr />
    <template v-for="item in items">
      <ChildComponent v-show="isShow" :key="item.id"></ChildComponent>
    </template>
    <button @click="count++">Add to count</button>
    <p>{{ count }}回クリックしました</p>
    <p v-if="id === 12">1</p>
    <p v-else-if="id === 2">2</p>
    <template v-else-if="id === 3">
      <p>2-1</p>
      <p>2-2</p>
      <p>2-3</p>
    </template>
    <p v-else>other</p>
    <ul>
      <template v-for="item in items">
        <li :key="item.id">
          {{ item.title }}
        </li>
      </template>
    </ul>
  </div>
</template>

<script>
import ChildComponent from "./ChildComponent";
export default {
  components: {
    ChildComponent,
  },
  //es6のメソッド記法
  data() {
    return {
      message: "<span>Hello Vue</span>",
      isShow: true,
      id: 3,
      count: 0,
      classObject: {
        "is-green": true,
      },
      items: [
        {
          id: this.$uuid.v4(),
          title: "1番目のリスト",
        },
        {
          id: this.$uuid.v4(),
          title: "２番目のリスト",
        },
        {
          id: this.$uuid.v4(),
          title: "3番目のリスト",
        },
      ],
    };
  },
};
</script>

<style scoped>
.is-green {
  color: green;
}
hr {
  margin: 16px 0;
}
</style>
