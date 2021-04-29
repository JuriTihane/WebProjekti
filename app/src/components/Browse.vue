<template>
    <div>
        <h2>Posts</h2>
        
        
        
            <div v-for="author in authors" :key="author.id" >
                <h3> {{author}} </h3>                    
            </div>
        
    </div>
    
</template>

<script>


export default {

    name: 'Browse',

    props: {
        authors: Array,
        questions: Array,
    }

}
</script>

<style>

</style>