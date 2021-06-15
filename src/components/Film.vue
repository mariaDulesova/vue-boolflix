<template>
    <div class="d-flex flex-column mx-2 my-4 p-2 movie-container"> 
        <h5> <span>Title: </span> {{ inputs.title || inputs.name}}</h5>
        <h6> <span>Original Title:</span> {{ inputs.original_title || inputs.original_name}}</h6>
        <div class="language">
            <span> Language: </span>
            <img src="../assets/img/en.png" alt="GB Flag"
                v-if="(inputs.original_language =='en')">
            <img src="../assets/img/it.png" alt="IT Flag"
                v-else-if="(inputs.original_language =='it')">
            <p v-else>{{ inputs.original_language }}</p>
        </div>
        <p><span>Votation: </span>{{ inputs.vote_average }}</p>
    </div>
</template>

<script>
export default {
    name: 'Film',
    props: ['inputs'],
    
}
</script>

<style scoped lang='scss'>
    .movie-container{
        width: calc(100% / 4);
        background-color: black;

        .language{
            img{
                width: 20px;
            }
        }
    }
    span{
        color:darkred;
    }
    
</style>