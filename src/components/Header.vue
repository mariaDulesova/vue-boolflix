<template>
    <nav class= "d-flex justify-content-between align-items-center px-4">
        <img src="../assets/img/logo.png" alt="">

        <div class="input-group mb-3 w-25 h-50">
            <input type="text" class="form-control" placeholder="Type to search..." aria-label="Type to search" aria-describedby="button-addon2"
            v-model="text"
            @keyup="$emit('performSearch', text)">

            <button class="btn btn-outline-danger ms-2" type="button" id="button-addon2"
            @click.prevent = "$emit('performSearch', text)">Search</button>
        </div>
    </nav>
    
</template>

<script>
export default {
    name: 'Header',
    data: function(){
        return {
            text:'',
            
        }
    }

}
</script>

<style scoped lang='scss'>
    nav {
        height: 80px;
        background-color: black;

        img {
            height: 95%;
        }
    }


</style>