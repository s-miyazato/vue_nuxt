<template>
  <div class="hello">
    <h1>{{ title }}</h1>
    <pre>{{ message }}</pre>
    <hr>
    <ol><slot /></ol>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    props: {
      title: String,
    },

    data: function() {
      return {
        message: 'This message ',
      };
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.area {
  width: 300px;
  height: 100px;
  background-color: #ddd;
  padding: 10px;
  font-size: 20pt;
}

.area:hover {
  cursor: pointer;
}

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

pre {
  font-size: 14pt;
  line-height: 1.25;
}

div.out {
  padding: 5px 0;
  background-color: #eee;
  width: 300px;
  height: 200px;
}

div.out:hover {
  cursor: pointer;
}

div.mid {
  padding: 5px 0;
  background-color: #ddd;
  width: 200px;
  height: 175px;
}

div.mid:hover {
  cursor: pointer;
}

div.in {
  padding: 5px 0;
  background-color: #ccc;
  width: 100px;
  height: 150px;
}

div.in:hover {
  cursor: pointer;
}

p.inner {
  color: red;
  font-size: 14pt;
}


</style>
