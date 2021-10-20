<template>

    <div class="resource-wrapper pt-8 w-4/6 grid grid-cols-1 mx-auto">
        <img v-for="item in data" :key="item" src="../../assets/img/hexagon.svg" alt="hexagonal shape with letter in it"
				 class="h-40 margin-adjust">
        <p v-for="item in data" :key="item">{{ item.properties.Name.title[0].text.content[0] }}</p>
        <ResourceCard v-for="(item, index) in data" :key="index" :aResource="item" class=" "/>
        <br>
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
    /* .margin-adjust:nth-child(odd) {
        transform: translateX(55%);
        
    }

    .margin-adjust:nth-child(even) {
        transform: translateY(-15%);
        
    }

    .margin-adjust:nth-child(3n) {
        transform: translate(55%, -15%);
    } */
    
    .margin-adjust:nth-child(even) {
        transform: translateX(65%);
        
    }

</style>