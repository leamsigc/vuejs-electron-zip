<template>
  <div class="alert-box">
    <h1>
      Please enter
      <br>a
      <br>valid ZipCode
    </h1>
    <button @click="closeWindows">OK</button>
  </div>
</template>
<script>
import { remote, ipcRender, ipcRenderer } from 'electron';

export default {
  name: 'AlertBox',
  methods: {
    closeWindows() {
      ipcRenderer.send('close-windows');
    },
  },
};
</script>
<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.alert-box {
  color: crimson;
  background: #eee;
  text-align: center;
  padding: 2rem 1em;
  text-transform: uppercase;

  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
button {
  padding: 0.5rem 3rem;
  font-weight: 900;
  border: 1px solid #fefefe;
  background: crimson;
  color: #f3f3f3;
  border-radius: 5px;
}
</style>
