<template>
	<div class="text-white container mx-auto mt-12">
	    <div>
	        <h1 class="text-center text-4xl my-12 uppercase">Resources</h1>
	    </div>
	    <h3 class="text-center text-2xl">A list of carefully curated resources for learning</h3>
		<br>
		<div>
			<ResourceBlock :data="resources"/>
		</div>
	</div>
</template>

<script>
	export default {
         async asyncData({ $axios }) {
            let resources = {};
			const filterData = { 
				filter: { property: "Status", select: { equals: "Published" } },
				sorts: [ { property: "Created", direction: "ascending" }]
			}
			resources = await $axios.$post('databases/e24c93ce3ea44cfd9a80b65bda42ba18/query', filterData)
			
			return { resources: resources.results }
		},
    }
</script>