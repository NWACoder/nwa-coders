<template>
    <div>
        <div class="flex-col self-center pt-2 text-center">
            <div class="group">
                <a class="text-lg" :href="aResource.properties.URL.rich_text[0].text.content" @mouseover="hover = true"  @mouseleave="hover = false">
                    {{ aResource.properties.Name.title[0].text.content }}
                </a>
                <div id="descriptionBox" v-if="hover" class="inline-block transition-opacity duration-500 opacity-50 ease-out group-hover:opacity-100">
                    <div class="w-96 bg-gray-200 border-gray-400 border-2 rounded-md absolute translate-x-40">
                        <p class="">{{aResource.properties.Description.rich_text[0].text.content}}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>        
</template>

<script>
    
    export default {
        props: ['aResource'],

        data() {
            return {
            hover: false,
            };
        },
    }
    
</script>

<style>
  
</style>
