<template>
  <div id="app">
    <div id="app">
      <HelloWorld title="slot">
        <li
          v-for="obj in slotobjs"
          v-bind:key="obj.name">
          {{ obj.name }} ({{ obj.mail }})
        </li>
      </HelloWorld>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  },

  data: function() {
    return {
      slotobjs: [
        {name: 'Taro', mail:'taro@yamada'},
        {name: 'Hanako', mail:'hanako@flower'},
        {name: 'Sachiko', mail:'sachiko@happy'},
      ]
    };
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin: 5px;
}

tr td {
  padding: 5px;
  border: 1px solid gray;
}

tr th {
  padding: 5px;
  border: 1px solid gray;
}

tr th.head {
  background: black;
  color: white;
}

</style>
