<template>
    <main>
        <div class="d-flex justify-content-center flex-wrap"
        :class ="(!visibility)?'d-none':''"> 
            <Film 
            v-for="(movie) in filteredMovies"
            :key="movie.id"
            :inputs ='movie'/>
        </div>
    </main> 
</template>

<script>
import axios from 'axios';
import Film from './Film';


export default {
    name: 'Main',
    components: {
        Film
    },
    props: ['searchedItem'],
    data:function(){
        return {
            movies: '',
            visibility: false,
            text: 'a'
        }
    },
    created: function() {
        axios
        .get('https://api.themoviedb.org/3/search/movie',{
            params: {
                api_key:'ee6f3e9d34bbe17cf718adc774f7aa29',
                query: `${this.text}`
            }
        })
        
        .then (
            result => {
                //this.text = this.searchedItem;
                this.movies = result.data.results;
                console.log(this.movies);
            }
        )
    },
    computed: {
        filteredMovies: function() {
            if(this.searchedItem == "") {
                return this.movies && this.visibility;
            } else {
                const newMovies = this.movies.filter (
                    element => {
                        this.visibility=true;
                        //this.text=this.searchedItem;
                        return element.title.toLowerCase().includes(this.searchedItem.toLowerCase());
                    }
                )
                return newMovies;
            }
        }
    }

}
</script>

<style scoped lang='scss'>
    main {
        height: calc(100vh - 80px);
        overflow:scroll;
    }

</style>