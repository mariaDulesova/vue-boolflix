<template>
    <div class="d-flex justify-content-center m-1 movie-container position-relative">
        <img :src="(inputs.poster_path == null)?'':addCover()" alt="Cover" 
        :class=" (inputs.poster_path == null)? 'd-none':'cover-poster'">
        <div class="d-flex flex-column position-absolute p-4 text-container">
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
    </div>
</template>

<script>
export default {
    name: 'Film',
    props: {
        'inputs': Object
    },
    methods: {
        addCover: function() {
            const webLink = 'https://image.tmdb.org/t/p/';
            const coverWidth = 'w185';
            return `${webLink}${coverWidth}${this.inputs.poster_path}`;
        }
    }

}
</script>

<style scoped lang='scss'>
    .movie-container{
        cursor: pointer;
        overflow: hidden;
        min-width: 185px;


        &:hover .cover-poster{
            opacity: 0.1;
        }

        .cover-poster {
            width:100%;
            opacity: 1;
            z-index: 9999;
            transition: all 0.2s linear;
        }

        .language{
            img{
                width: 20px;
            }
        }

        .text-container {
            height: 100%;
            width: 100%;
            background-color: rgb(0, 0, 0, 0.9);
        }

    }
    span{
        color:white;
    }

</style>