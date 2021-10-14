<template>
  <div class="outer">
    <div class="block">
      <div class="inner">
        <Header/>
        <hr/>
        <credit-calc />
        <hr />
        <ToDo />
        <hr/>
      </div>
    </div>
  </div>
</template>

<script>
import ToDo from './components/ToDo';
import Header from "./components/Header";
import CreditCalc from "./components/CreditCalc";
export default {
  name: 'App',
  components: {
    ToDo,
    Header,
    CreditCalc,
  },
  data: () => ({
    inputCountTerm: 1,
  })
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
}
body {
  height: 100%;
  padding: 0;
  background-color: aliceblue;
}
.outer {
  background-size: cover;
  height: 100%;
  box-sizing: border-box;
  display: flex;
  background-color: aliceblue;
  align-items: center;
 }
.block {
  display: block;
  text-align: start;
  background-color: aliceblue;
  box-shadow: 0 0 10px rgba(0,0,0,0.5);
  margin: 5% 0 0 30%;
  height: 100%;
  border-radius: 5%;
}

.inner {
  height: 100%;
  display: block;
  margin: 20px 20px 20px 20px;
}
</style>
