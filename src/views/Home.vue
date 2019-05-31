<template>
  <div class="home">
    <HelloWorld v-on:zipCode="getZipInfo" msg="Daytona Dev Solution"/>
    <div class="card__container">
      <InfoCards v-if="codeInformation" v-bind:codeInfo="codeInformation"/>
    </div>
  </div>
</template>

<script>
import { remote, ipcRender, ipcRenderer } from 'electron';
import axios from 'axios';
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import InfoCards from '../components/InfoCards';

export default {
  name: 'home',
  data() {
    return {
      codeInformation: null,
    };
  },
  components: {
    HelloWorld,
    InfoCards,
  },
  methods: {
    getZipInfo(code) {
      console.log(code);
      axios.get(`https://api.zippopotam.us/us/${code}`).then((data) => {
        if (data.status == 404) {
          ipcRenderer.send('toggle-box');
        }

        this.codeInformation = data.data.places;
        console.log(this.codeInformation);
      });
    },
  },
};
</script>
<style>
.card__container {
  background: rgba(254, 254, 254, 0.034);
  padding: 1rem 1rem;
  max-width: 800px;
  margin: 2rem auto 0;
}
</style>
