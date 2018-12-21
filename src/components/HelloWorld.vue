<template>
  <div class="hello">
    <a @click="downloadResult()">
Download Result
                  </a>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    downloadResult() {
      axios.get('http://localhost:3000/abc').then(({data}) => {
        const blob = new Blob([data], { type: 'application/pdf' });
        window.open(window.URL.createObjectURL(blob));
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
