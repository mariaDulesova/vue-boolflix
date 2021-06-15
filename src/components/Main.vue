<template>
    <main class="p-3">
        <div class="d-flex justify-content-center flex-wrap">
        <!-- :class ="(!visibility)?'d-none':''" -->
            <Film 
            v-for="(item) in searchedItems"
            :key="item.id"
            :inputs ='item'/>
        </div>
    </main> 
</template>

<script>
//import axios from 'axios';
import Film from './Film';


export default {
    name: 'Main',
    components: {
        Film
    },
    props: ['searchedItems'],
    data:function(){
        return {

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