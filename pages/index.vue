<template>
	<div class="mt-12">
		<Hero/>
		<EventBlock :data="data"/>
		<!-- <NewsLetter/> -->
		<SpeakerCTA/>
		<!-- <Sponsors/> -->
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

			const dataHasrelations = await $axios.$post('databases/d9f93215943f4d6ea9e73ab3af2f569c/query', { 
				filter: { "and": [{property: "Speaker", relation: { is_not_empty: true }}, {property: "Status", select: { equals: "Published" }} ] }

			})

			const getSpeakers = await Promise.all(dataHasrelations.results
				.map(async (item) => {
					const speakerID = item.properties.Speaker.relation[0].id
					const speaker = await $axios.$get(`pages/${speakerID}`)
					return { id: speakerID, children: speaker } 
				})
			)

			data.results.map((block) => {
				if(block.properties.Speaker.relation.length > 0 ){
					block.Speaker = getSpeakers.find(
		        		(x) => x.id === block.properties.Speaker.relation[0].id
		      		)
				}
			    return block;
			})
	
			return { data: data.results }
		}

	}
</script>


