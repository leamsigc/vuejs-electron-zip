<template>
  <div class="hello">
    <h1 class="title">
      {{ msg }}
      <small>
        <br>Get your City Geolocation
        <br>
        <strong>longitude 📍 latitude</strong>
      </small>
    </h1>
    <SearchInput v-on:zipCode="getZipInfo"/>
  </div>
</template>

<script>
import axios from 'axios';
import SearchInput from './SearchInput';

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  components: {
    SearchInput,
  },
  created() {},
  methods: {
    getZipInfo(zip) {
      this.$emit('zipCode', zip);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.title {
  padding: 1rem 0.5rem;
  max-width: 25ch;
  margin: 0 auto 1rem;
}
small {
  font-size: 0.9rem;
  line-height: 1;
}
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
