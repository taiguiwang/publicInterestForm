<template>
<div>
  <div>
    <Normalform/>
  </div>

  <div>
    <Logolink/>
  </div>

  <div>
    <Popup/>
  </div>

  <div>
    <Graphic/>
    <!-- <Test/> -->
  </div>
</div>

</template>

<script>
import Normalform from './components/Normalform.vue';
import Logolink from './components/Logolink.vue';
// import Test from './components/Test.vue';
import Popup from './components/Popup.vue';
import Graphic from './components/Graphic.vue';


export default {
  name: 'App',
  components: {
    Normalform,
    Logolink,
    Popup,
    Graphic,
    // Test,

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  color: white;
}
div{
  display: flex;
  margin-right: 20px;
}
</style>
