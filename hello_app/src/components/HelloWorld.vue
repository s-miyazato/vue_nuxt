<template>
  <div class="hello">
    <h1>{{ title }}</h1>
    <p>{{ message }}</p>
    <hr>
    <p>val: {{ val }}</p>
    <div>*2： <input type="number" v-model="a" name="" id=""></div>
    <div>^2： <input type="number" v-model="b" name="" id=""></div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    title: String,
  },
  data:function() {
    return {
      message: 'バリデーションチェック',
      val: 0,
    };
  },

  computed: {
    a: {
      get: function() {
        return this.val * 2;
      },
      set: function(value) {
        return this.val = Math.floor( value / 2);
      },
    },
    b: {
      get: function() {
        return this.val * this.val;
      },
      set:function(value) {
        this.val = Math.floor(Math.sqrt(value));
      },
    },
  },
  created: function() {
    this.val = 10;
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {
  margin: 0;
  padding: 0;
  text-align: left;
}

h1 {
  font-size: 72pt;
  font-weight: bold;
  text-align: right;
  letter-spacing: -8px;
  color: -8px;
  color: #f0f0f0;
  margin: 0;
}

p {
  margin: 0;
  color: #666;
  font-size: 16pt;
}
</style>
