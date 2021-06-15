<template>
    <div id="app">
      <Header 
      @performSearch="searchSelectedMovie"/>
      
      <Main 
      :searchedItems="allFilms"/> 
    </div>
</template>

<script>
import axios from 'axios';
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
      searchFieldText:'',
      moviesApiUrl: 'https://api.themoviedb.org/3/search/movie',
      seriesApiUrl: 'https://api.themoviedb.org/3/search/tv',
      apiKey: 'ee6f3e9d34bbe17cf718adc774f7aa29',
      movies:'',
      series: '',
      allFilms: ''
    }
  },
  methods: {
    searchSelectedMovie: function(text) {
      if(text.trim() == '') {
          this.allFilms=[];

        } else {
          axios.all([

              //Movies
              axios.get(this.moviesApiUrl,{
                params: {
                  api_key:this.apiKey,
                  query: text
                }
              }),

              //Series
              axios.get(this.seriesApiUrl, {
                params: {
                  api_key: this.apiKey,
                  query:text
                }
              })
            ])
          .then(axios.spread((...results) => {
              this.movies=results[0].data.results;
              this.series=results[1].data.results;
             console.log(this.movies, this.series)
            })
          )
          .catch(
            (error) => {
              console.log('Errore:', error)
            }
          )
          return this.allFilms = this.movies.concat(this.series)
        }
      }
    }
  }
</script>

<style lang="scss">
  @import './style/general.scss'
</style>
