<template>
  <div>
    <h1 v-html="leads.message" :class="classObject"></h1>
    <p>{{ leads.description }}</p>
    <button @click="addDescription">add description</button>
    <button @click="changeTextSize">large</button>
    <hr />
    <child-component v-show="isShow">
      <template v-slot:head>
        <p>head slot</p>
      </template>
      <template v-slot:default>
        <p>main slot</p>
        <p>main slot2</p>
      </template>
      <template v-slot:foot>
        <p>foot slot</p>
      </template>
    </child-component>
    <hr />
    <p v-if="id === 1">1</p>
    <template v-else-if="id === 2">
      <p>2-1</p>
      <p>2-2</p>
      <p>2-3</p>
    </template>
    <p v-else>Other</p>
    <hr />
    <template v-for="item in items">
      <child-component :title="item.title" :key="item.id">
        <span>slot content</span>
      </child-component>
    </template>
    <hr />
    <button @click="incrementCount">Add to count</button>
    <p>{{ count }}回クリックされました</p>
    <hr />
    <form action="#">
      <div>
        <span>名前：</span>
        <input
          type="text"
          :value="form.name"
          @input="form.name = $event.target.value"
        />
        <p>name: {{ getInputName }}</p>
      </div>
      <div>
        <span>性別: </span>
        <label>
          <input type="radio" value="male" v-model="form.sex" />
        </label>
        <label>
          <input type="radio" value="female" v-model="form.sex" />
        </label>
        <p>性別: {{ getRadioValue }}</p>
      </div>
      <div>
        <select v-model="form.selected">
          <option disabled value="">--出身地を選択してください--</option>
          <option
            v-for="option in form.options"
            :key="option.id"
            :value="option.value"
            >{{ option.value }}</option
          >
        </select>
        <p>出身地:{{ getSelectValue }}</p>
      </div>
      <div>
        <label for="">
          <input type="checkbox" v-model="form.checked">
          20歳です
        </label>
        <p>{{ getCheckBoxValue }}</p>
      </div>
    </form>
    <input type="text" v-model="inputText" />
    <p>computed: {{ getUpperCaseText }}</p>
    <p>methods: {{ showUpperCaseText() }}</p>
    <hr />
    <template v-for="category in categories">
      <p :key="$uuid.v4()">
        {{ category }}
      </p>
    </template>
    <button @click="updateText">update text</button>
  </div>
</template>

<script>
import ChildComponent from "./ChildComponent";
export default {
  //es6のメソッド記法
  data() {
    return {
      leads: {
        message: "<span>Hello Vue</span>",
        description: "",
      },
      message: "<span>Hello Vue</span>",
      isShow: true,
      description: "",
      id: 2,
      count: 0,
      inputText: "",
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
      form: {
        name: "",
        sex: "",
        selected: "",
        options: [
          {
            id: this.$uuid.v4(),
            value: "東京",
          },
          {
            id: this.$uuid.v4(),
            value: "埼玉",
          },
          {
            id: this.$uuid.v4(),
            value: "千葉",
          },
          {
            id: this.$uuid.v4(),
            value: "神奈川",
          },
        ],
        checked: false,
      },
      categories: ["Javascript", "jQuery"],
    };
  },
  methods: {
    incrementCount() {
      this.count++;
    },
    showUpperCaseText() {
      const upperCaseText = this.inputText.toUpperCase();
      // console.log(`method: ${upperCaseText}`);
      return upperCaseText;
    },
    addDescription() {
      this.leads.description = "vue-lesson";
      // console.log(this);
      // console.log(this.description);
    },
    updateText() {
      // this.categories.splice(1, 1, "Vue.js");
      this.$set(this.categories, 1, "Vue.js");
    },
    changeTextSize() {
      // this.classObject = Object.assign({}, this.classObject, {
      //   'is-large': true,
      // })
      // this.classObject = {...this.classObject, 'is-large': true}
      this.$set(this.classObject, "is-large", true);
    },
  },
  computed: {
    getUpperCaseText() {
      const upperCaseText = this.inputText.toUpperCase();
      // console.log(`computed: ${upperCaseText}`);
      return upperCaseText;
    },
    getInputName() {
      return this.form.name;
    },
    getRadioValue() {
      return this.form.sex;
    },
    getSelectValue() {
      return this.form.selected;
    },
    getCheckBoxValue() {
      return this.form.checked;
    }
  },
  watch: {
    inputText(value, oldValue) {
      console.log(`value: ${value}`);
      console.log(`oldValue: ${oldValue}`);
    },
    leads: {
      handler() {
        console.log("add description");
      },
      deep: true,
    },
  },
  components: {
    ChildComponent,
  },
};
</script>

<style scoped>
.is-green {
  color: green;
}
.is-large {
  font-size: 48px;
}
hr {
  margin: 16px 0;
}
</style>
