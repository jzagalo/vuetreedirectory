<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <TreeBrowser :node="root" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import TreeBrowser from './components/TreeBrowser.vue';

@Component({
  components: {
    TreeBrowser,
  },
})
export default class App extends Vue {
  public root: any  =  {
      name: '/',
      children: [
        {
          name: 'music',
          children: [
            {
              name: 'song.mp3'
            },
          ]
        },
        {
          name: 'workspace',
          children: [
            {
              name: 'source.js'
            },
          ]
        }
      ]
  };
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
