<template>
<div>
  <h2>
  Расчёт кредита (Дифференцированная схема)
  </h2>
  <form @submit.prevent class="innerAndButton">
    <input class="colorfun" type="number" v-model="summer"  placeholder="Сумма (руб)">
    <input class="colorfun" type="number" v-model="year"  placeholder="Время (год)">
    <input class="colorfun" type="number" v-model="percent"  placeholder="Проценты">
    <button class="gamburger" v-on:click="currentRes">Рассчитать!</button>
  </form>
  <div>
    Общая выплата: {{ result }}
  </div>
  <div v-for="item in payments" :key="item.id">
    <div> ежемесячный платёж {{item}}</div>
  </div>
</div>
</template>

<script>
export default {
  name: "CreditialCalc",
  data: () => {
    return {
      summer: 0,
      year: 0,
      percent: 0,
      result: 0,
      arr: [],
      payments: [],
      monthPay: 0,
    }
  },
  methods: {
    currentRes(){
      let sumPayments = 0;
      let everyMonthPay = this.year * 12;
      let rest = this.summer;
      let realMonthPay = rest / (this.year * 12.0);

      while ( everyMonthPay !== 0 ) {
        let mp = realMonthPay + (rest * this.percent / 1200)
        this.payments.push(Math.round(mp))
        rest = rest - realMonthPay
        everyMonthPay = everyMonthPay - 1
      }
      for (let i = 0; i < this.payments.length; i++) {
        sumPayments += this.payments[i];
      }
      this.result = sumPayments;
    }
  }
}
</script>

<style scoped>
.innerAndButton {
  margin: 10px;
}

#area input{
  color: #000000;
}
#area button{
  color: #000000;
}
.gamburger {
  margin-left: 10px;
  color: black;
  background-color: #abb6bd;
  border: none;
  box-shadow: 0 0 10px rgba(0,0,0,0.5);
}
.colorfun {
  background-color: aliceblue;
  color: #000000;
  border: none;
  box-shadow: 0 0 10px rgba(0,0,0,0.5);
  margin: 10px;
}
</style>