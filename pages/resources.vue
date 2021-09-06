<template>
    <div class="container mx-auto mt-12 p-0.5 ">
        <h1 class="text-center text-4xl my-10 uppercase">Resources</h1>
        <hr class=" mx-44 flex self-center">
        <h3 class="text-center text-2xl my-10">A community currated list of helpful resources & communites</h3>

        <div class="bg-gray-100 h-96 rounded-lg shadow-lg border-r-2">
            <div v-for="item in resources" :key="item.Name" class="flex-col justify-items-center">
                <a class="mx-auto" :href="item.properties.URL.rich_text[0].text.content">
                    <p class="text-lg text-center pt-2">{{item.properties.Name.title[0].text.content}}</p>
                </a>
            </div>
            
        </div>
        
    </div>
    
</template>
 
<script>
    let resources = [];
    export default {
        async asyncData({ $axios }) {
			// let resources = {};
            // const title = [];
            const filterData = { 
				filter: { property: "Status", select: { equals: "Published" } }
			};	
			resources = await $axios.$post('databases/e24c93ce3ea44cfd9a80b65bda42ba18/query', filterData);
            
            console.log(resources.results) 
			return { resources: resources.results }
	    },
        // props: {
        //     url: 
        // }
        // item.properties.URL.rich_text.text.content for link
    }
       
</script>
        
    

<style>

</style>