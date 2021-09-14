<template>
  <div class="hello">
    <h1>{{ title }}</h1>
    <p>{{ message }}</p>
    <hr>
    <div>
      <textarea v-model="fomula" cols="40" rows="5"></textarea>
    </div>
    <div>
      <button v-on:click="doAction">CALC</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Calc',
  props: {
    title: String,
  },
  data:function(){
    return {
      message: 'Enter expression:',
      fomula:'0',
    };
  },
  methods: {
    doAction: function() {
      let arr = this.fomula.trim().split('¥n');
      let last = arr.pop();
      let fn = '';
      for(let n in arr) {
        if (arr[n].trim() != '') {
          fn += 'var' + arr[n] + ';';
        }
      }
      fn += 'return ' + last + ';';
      let exp = 'function f() {' + fn + '} f();';
      let ans = eval(exp);
      this.message = 'answer：' + ans;
      let re = arr.join(';').trim();
      if (re != '') { re += ';'}
      re += last;
      this.$emit('result-event', re, ans);
    }
  }
}
</script>