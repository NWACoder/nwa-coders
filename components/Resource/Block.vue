<template>

    <div class="resource-wrapper pt-8 w-full grid grid-cols-1 mx-auto ml-20">
        <div v-for="(item, index) in data" :key="index" class=" margin-adjust relative mb-12">
            <ResourceCard :aResource="item" class=""/>
        </div>  
    </div>
</template>

<script>
     export default {
        props: { 
            data: [] 
        },
    }
</script>

<style>
    .margin-adjust:nth-child(even) {
        margin-left: 9%;
        margin-top: 1%;
    }
    
    
</style>