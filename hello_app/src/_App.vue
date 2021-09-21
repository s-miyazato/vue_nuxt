<template>
  <div id="app">
    <Calc v-bind:title="message" v-on:result-event="appAction" />
    <hr>
    <div>
      <table>
        <tr>
          <th class="head">Expression</th>
          <th class="head">Value</th>
          <th class="head">btn</th>
        </tr>
        <tr v-for="(result,i) in results" :key="result">
          <td>{{ result[0] }}</td>
          <td>{{ result[1] }}</td>
          <td>
            <button v-on:click="remove(i)">clear</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import Calc from './components/Calc.vue'

export default {
  name: 'app',
  components: {
    Calc
  },

  data: function() {
    return {
      message: 'CALC',
      results: [],
    };
  },

  
  created: function() {
    let items = localStorage.getItem('log');
    if (!items) return
    let logs = JSON.parse(items);
    if (logs != null) {
      this.results = logs;
    }
  },

  methods: {
    appAction: function(exp, res) {
      this.results.unshift([exp,res]);
      if (this.results.length > 10) {
        this.results.pop();
      }
      this.setLocalStorage()
    },

    remove: function(i) {
      this.results.splice(i,1)
      //localStorage.removeItem('log')
      this.setLocalStorage()
    },

    setLocalStorage: function() {
      let log = JSON.stringify(this.results);
      localStorage.setItem('log', log);
    }
  }
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
