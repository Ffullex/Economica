<template>
  <div id="area">
    <p class="innerAndButton">Введите текст:
      <input class="colorfun" type="text" v-model="userText"  placeholder="Сам такой">
      <button class="gamburger" v-on:click="add" > Добавить </button>
      <button class="gamburger" v-on:click="clearAll">Удалить</button>
    </p>

    <div class="filter">Фильтровать по
      <select class="colorfun" v-model="filterParameter">
        <option value="checkOn">Выполненные</option>
        <option value="checkOff">Невыполненные</option>
        <option value="priority">По имени</option>
      </select>
      <button class="gamburger" v-on:click="filter">Фильтровать</button>
    </div>

    <div v-for="item in list" id="list" :key="item.id">
        <Element :element="item" :clear="clear"/>
    </div>
  </div>
</template>

<script>
import Element from "./Element";
export default {
  name: "ToDo",
  components: {
    Element
  },
  data: () => ({
    userText: '',
    list: [],
    filteredList: [],
    id: 1,
    filterParameter: '1',
    elementCheck: true,
  }),
  methods: {
    add: function () {
      console.log(this.id);
      console.log(this.userText);
      this.list
          .push({
            id: this.id,
            title: this.userText,
          });
      console.log(this.id);
      console.log(this.userText);
      this.userText = '';
      this.id += 1;
      console.log(this.id);
      console.log(this.userText);
    },
    clearAll: function () {
      this.list = []
      this.id = 1;
    },
    clear: function (id) {
      this.list = this.list.filter(element => element.id !== id)
    },
    filter: function () {
      switch (this.filterParameter){
        case 'checkOn':
          return (this.filteredList = this.list.filter(element => {element.title}))
        case 'checkOff':
          return console.log('work2')
        case 'priority':
          return console.log('work3')
      }
    }

  }
}

</script>

<style scoped>
.innerAndButton {
  margin: 10px;
}
.filter {
  margin: 10px;
}
#area{
  min-width: 500px;
  color: #000000;
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
}
</style>