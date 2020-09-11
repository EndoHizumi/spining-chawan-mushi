<template>
  <div id="parent">
    <img v-for="food in foodList" v-bind:key="food" v-bind:src="loadPic()" />
  </div>
</template>

<script>
export default {
  data() {
      return{
          foodList: [],
          count: 0,
          advance: 0,
          positionList:['leftTop','leftBottom','rightTop','rightBottom']
      }
  },
  props: {
    deg: Number,
    filePath: String,
  },
  methods: {
      append: function(params) {
          this.count++
          if (this.count > 4){
              this.foodList.push(this.positionList[this.count])
          }
      }
  }
};
</script>

<style>
</style>