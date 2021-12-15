<template>
  <div class="outer">
    <div class="block">
      <div class="inner">
        <Header/>
        <hr/>
        <credit-calc />
        <hr/>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import CreditCalc from "./components/CreditCalc";
export default {
  name: 'App',
  components: {
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
  margin: auto;
  height: 100%;
  display: flex;
  background-color: aliceblue;
 }
.block {
  display: block;
  background-color: aliceblue;
  box-shadow: 0 0 10px rgba(0,0,0,0.5);
  margin: auto;
  height: 100%;
  border-radius: 15px;
}

.inner {
  height: 100%;
  display: block;
  margin: 20px 20px 20px 20px;
}
</style>
