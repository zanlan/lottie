<template>
    <div id="app">
        <lottie  class="demo" :options="defaultOptions1" :height="400" :width="400" v-on:animCreated="handleAnimation"/>
        <lottie  class="demo" :options="defaultOptions2" :height="400" :width="400" v-on:animCreated="handleAnimation"/>
        <div>
            <p>Speed: x{{animationSpeed}}</p>
            <input type="range" value="1" min="0" max="10" step="0.5"
                   v-on:change="onSpeedChange" v-model="animationSpeed">
        </div>
    </div>

</template>

<script>
  import Lottie from './lottie.vue';
  import * as animationData1 from './assets/zl1.json';
  import * as animationData2 from './assets/zl2.json';

  export default {
    name: 'app',
    components: {
      'lottie': Lottie
    },
    data() {
      return {
        defaultOptions1: {animationData: animationData1},
        defaultOptions2: {animationData: animationData2},
        animationSpeed: 1,
        anim:null
      }
    },
    methods: {
      handleAnimation: function (anim) {
        this.anim = anim;
      },
      onSpeedChange: function () {
        this.anim.setSpeed(this.animationSpeed);
      }
    }
  }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
    .demo{
      border: 2px solid lime;
    }
    h1, h2 {
        font-weight: normal;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
