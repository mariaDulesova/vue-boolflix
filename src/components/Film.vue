<template>
    <div class="d-flex justify-content-center m-1 movie-container position-relative">
        <!-- Cover -->
        <img :src="(inputs.poster_path == null)?'':addCover()" :alt="inputs.title || inputs.name" 
        :class=" (inputs.poster_path == null)? 'd-none':'cover-poster'">
        <!-- /Cover -->
        <!-- BackCover -->
        <div class="d-flex flex-column position-absolute p-4 text-container">
            <h5> <span class="fw-bold">Title: </span> {{ inputs.title || inputs.name}}</h5>
            <p> <span class="fw-bold">Original Title:</span> {{ inputs.original_title || inputs.original_name}}</p>
            <div class="language">
                <span class="fw-bold me-2">Language:</span>
                <!-- Soluzione 1: va bene se ci sono 1-2 bandiere-->
                <img src="../assets/img/en.png" alt="GB Flag"
                    v-if="(inputs.original_language =='en')">
                <img src="../assets/img/it.png" alt="IT Flag"
                    v-else-if="(inputs.original_language =='it')">
                <span v-else>{{ inputs.original_language }}</span>
                <!-- Soluzione 2 -->
                <!-- <img 
                src="require(..`assets/img/${inputs.original_language}.png`)" 
                alt="`${inputs.original_language}`"
                v-if="availableFlags.includes(inputs.original_language)">
                <p v-else>{{ inputs.original_language }}</p>-->
            </div>
            <div class="d-flex">
                <div v-for="(n) in 5" :key="n">
                    <i class="fa-star my-3"
                    :class="(n<=setFullStars)?'fas':'far'"></i>
                </div>
            </div>
            <div>
                <span class="fw-bold">Overview:</span> 
                <p>{{ setOverview() }}</p>
            </div>
        </div>
        <!-- /BackCover -->
    </div>
</template>

<script>

export default {
    name: 'Film',
    props: {
        'inputs': Object
    },
    data:function(){
        return {
            availableFlags: ['it', 'en']
        }
    },
    computed: {
        setFullStars: function(){
            return Math.round((this.inputs.vote_average)/2);   
        }
    },
    methods: {
        addCover: function() {
            const webLink = 'https://image.tmdb.org/t/p/';
            const coverWidth = 'w342';
            return `${webLink}${coverWidth}${this.inputs.poster_path}`;
        },
        setOverview: function() {
            if(this.inputs.overview.length>=300) {
                return this.inputs.overview.slice(0, 300)+'...'
            } else {
                return this.inputs.overview;
            }
        }
    }
}
</script>

<style scoped lang='scss'>
    .movie-container{
        cursor: pointer;
        overflow: hidden;
        min-width: 342px;
        border-radius: 5px;

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

        span{
        color:white;
    }
    }
    
    .fa-star {
        color: rgb(255, 174, 0);
    }
</style>