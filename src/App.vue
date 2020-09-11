<template>
  <div id="app">
    <div id="header">
      <h1>Welcome to chawan-mushi App</h1>
      <p>{{message}}</p>
    </div>
    <div id="controller">
      <span id="nowState">state:</span>
      <button id="rotateControll" v-on:click="toggle">{{state}}</button>
      <p>
        <span>chawan-mushi:{{index}} yen</span>
        <br />
        <button id="add" v-on:click="add_sushi">+</button>
        <button id="reduce" v-on:click="reduce_sushi">-</button>
      </p>
    </div>
    <ul>
      <li v-for="food in foods" v-bind:key="food.id" v-on:click="onchange(food.id)">
        <sushi v-bind:class="food.class" v-bind:state="food.state" v-bind:name="food.name" v-bind:food="food.icon" />
      </li>
    </ul>
  </div>
</template>

<script>
import sushi from "./components/chawan-mushi";
export default {
  name: "app",
  data() {
    return {
      state: "spin",
      message:
        "Japanese Common People Supporter is kaiten-zushi. I expressed gratitude for that kaiten-zushi.",
      foods: []
    };
  },
  components: {
    sushi
  },
  mounted: function() {
    this.foods.push({
      id: 1,
      state: this.state,
      name: "sushi",
      icon: "Chawan-Mushi.png"
    });
  },
  computed: {
    index: function() {
      return this.foods.length * 100;
    }
  },
  methods: {
    toggle() {
      // 切り替え
      if (this.state == "spin") {
        this.state = "stop";
        this.message = "oh? were you full of stomach?";
      } else {
        this.state = "spin";
        this.message =
          "Japanese Common People Supporter is kaiten-zushi. I expressed gratitude for that kaiten-zushi.";
      }
      // 寿司だけに切り替え結果を適用する
      this.foods
        .filter(food => food.name == "sushi")
        .forEach(sushi => {
          sushi.state = this.state;
        });
    },
    add_sushi() {
      var foodNum = this.foods.length;
      this.foods.push({
        id: foodNum,
        state: "satellite",
        name: "sushi",
        icon: "Chawan-Mushi.png"
      });
    },
    reduce_sushi() {
      if (this.foods.length > 1) {
        this.foods.pop();
      }
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

ul li {
  display: inline;
}
</style>
