<template>
    <main>
        <!-- Display before film search started -->
        <div class="d-flex justify-content-center align-items-center home-container"
        v-if="searchedItems.length==0">
            <Home/>
        </div>
        <!-- /Display before film search started -->
        <!-- Display films searched -->
        <div class="d-flex justify-content-center flex-wrap m-3"
        v-else>
            <Film 
            v-for="(item) in searchedItems"
            :key="item.id"
            :inputs ='item'/>
        </div>
        <!-- /Display films searched -->
    </main> 
</template>

<script>
import Home from './Home'
import Film from './Film';


export default {
    name: 'Main',
    components: {
        Home,
        Film
    },
    props: ['searchedItems'],    
}
</script>

<style scoped lang='scss'>
    main {
        height: calc(100vh - 80px);
        overflow:scroll;
        background-color: rgb(51, 51, 51);

        .home-container{
            height: 100%;
            background-image:linear-gradient(rgba(0, 0, 0, 0.2),rgba(0, 0, 0, 0.2)), url(https://help.nflxext.com/0af6ce3e-b27a-4722-a5f0-e32af4df3045_what_is_netflix_5_en.png);
            background-position: center;
            background-size: cover;
        }

    }
</style>