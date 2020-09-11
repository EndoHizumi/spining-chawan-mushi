<template>
  <div>
    <div v-bind:class="[state,name]" id="sushi"><img v-bind:src="loadPic()"></div>
  </div>
</template>

<script>
export default {
  props: {
    name: String,
    state: String,
    food: String
  },
  methods: {
    loadPic:function(){
      return require(`@/assets/${this.food}`)
    }
  }
};
</script>

<style>
.sushi {
  margin-left: auto;
  margin-right: auto;
  display: inline-block;
}

.spin {
  animation: spin 5s linear infinite;
}

.sushi.stop {
  filter: grayscale(100%);
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>

