<template>
  <div>
    <input type="checkbox" >
      <span>{{element.id + '.'}}{{element.title + ''}}</span>
    <button class="gamburger" v-on:click="clear(element.id)">Удалить</button>
  </div>
</template>

<script>
export default {
  name: "Element",
  props: {
    clear: Function,
    element: Object,
  },

}

</script>

<style scoped>
.gamburger {
  margin-left: 10px;
  color: black;
  background-color: #abb6bd;
  border: none;
  box-shadow: 0 0 10px rgba(0,0,0,0.5);
}
</style>