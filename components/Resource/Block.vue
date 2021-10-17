<template>
    <div class="resource-wrapper grid grid-cols-2 gap-4">
        <ResourceCard v-for="item in data" :key="item.id" :aResource="item"/>
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