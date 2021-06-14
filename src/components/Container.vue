<template>
    <div class="d-flex justify-content-center flex-wrap"> 
        <Film 
        v-for="(movie, id) in movies"
        :key="id"
        :inputs ='movie'/>
    </div> 
</template>

<script>
import axios from 'axios';
import Film from './Film';


export default {
    name: 'Container',
    components: {
        Film
    },
    data:function(){
        return {
            movies: ''
        }
    },
    created: function() {
        axios
        .get('https://api.themoviedb.org/3/search/movie',{
            params: {
                api_key: 'ee6f3e9d34bbe17cf718adc774f7aa29',
                query: 'forest'
            }
        })
        .then (
            result => {
                this.movies = result.data.results;
                console.log(this.movies);
            }
        )
    }

}
</script>

<style scoped lang='scss'>
    div {
        border: 1px solid black;
    }

</style>