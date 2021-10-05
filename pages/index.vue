<template>
	<div class="mt-12">
		<Hero/>
		<EventBlock :data="data"/>
		<!-- <Sponsors/> -->
		<NewsLetter/>
		<SpeakerCTA/>
		
	</div>
</template>

<script>
	export default {

		head() {
			return {
				title: 'NWA Coders',
				meta: [
					{
						hid: 'description',
						name: 'description',
						content: 'NWA Coders: Learn, Improve, Land a job '
					}
				]
			}
		},

		async asyncData({ $axios }) {
			
			let data = {}

			const filterData = { 
				filter: { property: "Status", select: { equals: "Published" } },


				// filter: { "and":  [ 
				// 		{ property: "Type", select: { equals: "Virtual" } }, 
				// 		{ property: "Status", select: { equals: "Published" } }
				// 	]
				// },


				sorts: [ { property: "Day", direction: "ascending" }]
			}
			
			data = await $axios.$post('databases/d9f93215943f4d6ea9e73ab3af2f569c/query', filterData)

			return { data: data.results }
		}

	}
</script>


