<template>
    <div class="container mx-auto mt-12 p-0.5">
        <h1 class="text-center text-4xl my-10 uppercase">Resources</h1>
        <hr class="mx-44 flex self-center" />
        <h3 class="text-center text-2xl my-10">
            A currated list of helpful resources & communites
        </h3>
        <div class="bg-gray-100 h-96 rounded-lg shadow-lg border-r-2 grid grid-cols-3 justify-items-center">
            <div class="..."></div>
            <ul class="...">
                <li v-for="item in resources" :key="item.id">
                    <ResourceItem class=""  :aResource="item"/>
                </li>
            </ul>
            <div class="...">
                <ResourceDescription :aResource="item"></ResourceDescription>
            </div>

        </div>
    </div>
</template>

<script>
export default {
    
    async asyncData({$axios}) {
        let resources = [];
        const filterData = {
            filter: {
                property: 'Status',
                select: {
                    equals: 'Published',
                },
            },
        }
        resources = await $axios.$post('databases/e24c93ce3ea44cfd9a80b65bda42ba18/query', filterData)
        return {
            resources: resources.results,  
        }
    },
    
}
</script>