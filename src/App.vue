<template>
  <div class="container" id="app">
    
    <SourceSelection v-on:sourceChanged="sourceChanged"></SourceSelection>
    <Newslist v-bind:source="source"></Newslist>
    
  </div>
</template>

<script>
import Newslist from './components/Newslist.vue'
import SourceSelection from './components/SourceSelection.vue'
export default {
  name: 'app',
  components: {
    Newslist,
    SourceSelection
  },
  data () {
    return {
      source: ""
    }
  },
  methods: {
    sourceChanged: function (source) {
      this.source = source;
    }
  }
}
</script>

<style>
  #app {
    padding-top: 20px
  }
</style>