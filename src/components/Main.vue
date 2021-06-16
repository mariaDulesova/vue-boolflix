<template>
    <main>
        <div class="d-flex justify-content-center align-items-center home-container"
        v-if="searchedItems.length==0">
            <Home/>
        </div>
        <div class="d-flex justify-content-center flex-wrap m-3"
        v-else>
            <Film 
            v-for="(item) in searchedItems"
            :key="item.id"
            :inputs ='item'/>
        </div>
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
            background-image: url(https://help.nflxext.com/0af6ce3e-b27a-4722-a5f0-e32af4df3045_what_is_netflix_5_en.png);
            background-position: center;
            background-size: cover;
            opacity: 0.9;
        }

    }
</style>