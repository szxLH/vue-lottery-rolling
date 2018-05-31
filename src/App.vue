<template>
  <div class="container">
    <lottery-rolling 
      :datasource="list"
      drawText="play"
      :canDraw="true"
    />
  </div>
</template>

<script>

import VueLotteryRolling from 'vue-lottery-rolling'
import 'vue-lottery-rolling/dist/vue-lottery-rolling.min.css'

export default {
  name: 'app',
  data () {
    return {
      
    }
  },
  computed: {
    list(){
      let data = [
        { src: require('./assets/AR.png'), desc: '0' },
        { src: require('./assets/AU.png'), desc: '1' },
        { src: require('./assets/BE.png'), desc: '2' },
        { src: require('./assets/BR.png'), desc: '3' },
        { src: require('./assets/CH.png'), desc: '4' },
      ]
      return [data, data, data];
    }

  },
  components: {
    'lottery-rolling': VueLotteryRolling
  }
}
</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
  }
  li {
    list-style: none;
  }
  .container {
    // border: 1px solid #f00;
    width: 500px;
    height: 300px;
  }
</style>
