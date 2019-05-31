<template>
  <form @submit="onSubmit">
    <label>
      <small>Enter a valid Zip code and get the geolocation</small>
    </label>
    <hr>
    <input type="text" placeholder="Enter a zip code" v-model="zip" name="zip">
    <button>Get Details</button>
  </form>
</template>

<script>
import { remote, ipcRender, ipcRenderer } from 'electron';

export default {
  name: 'SearchInput',
  data() {
    return {
      zip: '',
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      const isValidZip = /(^\d{5}$)|(^\d{5}-\d{4}$)/.test(this.zip);

      if (!isValidZip) {
        // Show alert box
        ipcRenderer.send('toggle-box');
        this.resetZip();
      } else {
        this.$emit('zipCode', this.zip);
        this.resetZip();
      }
    },
    resetZip() {
      this.zip = '';
    },
  },
};
</script>
<style scoped>
form {
  background: rgba(51, 51, 51, 0.445);
  color: #f3f3f3;
  padding: 2rem 1rem;
  font-size: 2rem;
}

input[type="text"],
button {
  padding: 0.8rem 1rem;
  margin-left: 0.5rem;

  border-radius: 5px;
  border: none;
}
button {
  background: #625aca;
  color: #f3f3f3;
}
</style>
