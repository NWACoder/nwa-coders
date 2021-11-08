<template>
	<div class="text-white container mx-auto mt-12 px-4 md:px-0 h-screen">
		<div>
			<h1 class="text-center text-4xl my-12 uppercase">Guest Speakers</h1>
		</div>
		 <div class="grid grid-cols-1 gap-4 lg:grid-cols-4">
			<SpeakerCard v-for="item in pages" :key="item.id" :speaker="item"/>
		</div>
	</div>
</template>

<script>
	export default {
		async asyncData({ $axios, params }) {
			
			let pages = {}

			const filterData = { 
				filter: { property: "Status", select: { equals: "Published" } }
			}
			
			pages = await $axios.$post('databases/815035805b6d4a53ab7a74c81ee7fa0b/query', filterData)
			
			return { pages: pages.results,  }
		}
	}
</script>