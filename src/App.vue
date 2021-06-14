<template>
    <div id="app">
      <Header 
      @performSearch="searchSelectedMovie"/>
      
      <Main 
      :searchedItem="searchFieldText"/> 
    </div>
</template>

<script>
import Header from './components/Header';
import Main from './components/Main';

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data: function(){
    return {
      searchFieldText:''
    }
  },
  methods: {
    searchSelectedMovie: function(searchMovie) {
      return this.searchFieldText = searchMovie;
      
    }
  }
}
</script>

<style lang="scss">
  @import './style/general.scss'
</style>
