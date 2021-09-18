<template>
        <div class="pt-2 text-center w-auto group">
            <a class="text-lg" :href="aResource.properties.URL.rich_text[0].text.content">
                {{ aResource.properties.Name.title[0].text.content }}
            </a>
            <p id="descriptionBox" class="hidden group-hover:block
            transition-opacity duration-1000 ease-out opacity-0 group-hover:opacity-100
            absolute top-2 right-0 z-10 w-96 bg-gray-200 border-gray-400 border-2 rounded-md">
            	{{aResource.properties.Description.rich_text[0].text.content}}
            </p>
        </div>
</template>

<script>
    
    export default {
        props: ['aResource'],
    }
    
</script>

<style>
  
</style>