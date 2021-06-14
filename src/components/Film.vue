<template>
    <div class="d-flex flex-column p-2"> 
        <h3>{{ inputs.title }}</h3>
        <h4>{{ inputs.original_title }}</h4>
        <p>{{ inputs.original_language }}</p>
        <p>{{ inputs.vote_average }}</p>
  
    </div>
</template>

<script>
export default {
    name: 'Film',
    props: ['inputs'],
    
}
</script>

<style scoped lang='scss'>
    div{
        width: calc(100% / 4);
    }
</style>