<template>
<div>
  <h2>
  Расчёт кредита (Дифференцированная схема)
  </h2>
  <form @submit.prevent class="innerAndButton">
    <input class="colorfun" type="number" v-model="summer"  placeholder="Сумма (руб)">
    <input class="colorfun" type="number" v-model="month"  placeholder="Время (месяцев)">
    <input class="colorfun" type="number" v-model="percent"  placeholder="Проценты">
    <button class="gamburger" v-on:click="currentRes">Рассчитать!</button>
  </form>
  <div class="result" v-if="result > 0">
    Общая выплата: {{ result }}
  </div>

<div class="table">
  <div class="table__col">
    Номер платежа
    <div v-for="item in counter" :key="item.id" class="table__column1">
      <div>{{item}}</div>
    </div>
  </div>

  <div class="table__col">
    Ежемесячный платёж
    <div v-for="item in payments" :key="item.id" class="table__column2">
      <div>{{item}}</div>
    </div>
  </div>

  <div class="table__col">
    Основной платёж
    <div v-for="item in payments" :key="item.id" class="table__column2">
      <div>{{mainpay}}</div>
    </div>
  </div>

  <div class="table__col">
    Проценты
    <div v-for="item in percents" :key="item.id" class="table__column2">
      <div>{{item}}</div>
    </div>
  </div>


  <div class="table__col">
    Остаток кредита
    <div v-for="item in balance" :key="item.id" class="table__column2">
      <div>{{item}}</div>
    </div>
  </div>
</div>
</div>
</template>

<script>
export default {
  name: "CredentialCalc",
  data: () => {
    return {
      summer: Number,
      month: Number,
      percent: Number,
      result: Number,
      count: 1,
      counter: [],
      payments: [],
      mainpay: Number,
      percents: [],
      balance: [],
      monthPay: 0,
    }
  },
  methods: {
    currentRes(){
      let S = this.summer;
      let n = this.month;
      let OD = this.summer;
      let i = Number((this.percent / 100).toFixed(2));
      let k =  12;
      let DP = Number((S/n).toFixed(2)) + Number((OD*i/k).toFixed(2));

      let balancir = this.summer;
      this.result = 0;
      this.counter.push(this.count);
      this.percents.push(Number((OD*i/k).toFixed(2)));
      this.balance.push(balancir);

      this.mainpay = Number((S/n).toFixed(2));
      while(OD) {
        OD = OD - Number((S/n).toFixed(2));
        if(OD >= 0) {
          console.log(this.count + ':::' + (OD*i/k).toFixed(2))
          this.payments.push(DP);
          this.percents.push(Number((OD*i/k).toFixed(2)));
          balancir -= DP;
          if (balancir <= 0) {
            balancir = 0;
          }
          this.balance.push(balancir);
          DP = Number((S / n).toFixed(2)) + Number((OD * i / k).toFixed(2));
          this.result += Number(DP);
          this.count += 1;
          this.counter.push(this.count);
          if(OD === 0) {
            this.counter.pop();
            this.balance.pop();
            this.percents.pop();
          }
        } else {
          this.counter.pop();
          this.balance.pop();
          this.percents.pop();
          break;
        }
      }
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
.result {
  margin-bottom: 40px;
}
.table {
  display: flex;
  width: 100%;
}
.table__col {
  margin-right: 20px;
}
.table__column1 {
  border-bottom: 1px solid gray;
}
.table__column2 {
  border-bottom: 1px solid gray;
}
</style>