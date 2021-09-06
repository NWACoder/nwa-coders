<template>
	<div class="bg-gray-100 p-0.5 rounded-lg shadow-lg border-r-2">
		<h2 class="text-2xl my-3 p-4 mx-auto rounded-md">Meet-up Schedule</h2>
		<div v-for="item in data.results" :key="item.id" class="block px-6">
			<div 
			:class="{ 'border-blue-800 border-4': getDate(item.properties.Day.date.start) }"
			 class="relative block rounded-lg border-2 border-gray-300 bg-white shadow-md px-6 py-4 cursor-pointer hover:border-gray-400 sm:flex sm:justify-between focus:outline-none mb-4">
				<div class="flex text-left">
					<div class="text-sm">
						<div class="font-medium text-gray-900">
							{{item.properties.Name.title[0].plain_text}}
						</div>
						<div class="text-gray-500">
							<p class="sm:inline">{{item.properties.Time.rich_text[0].plain_text}} CST</p>
						</div>
					</div>
				</div>
				<div class="mt-2 flex text-sm sm:mt-0 sm:block sm:ml-4 sm:text-right">
					<div class="font-medium text-gray-900">{{ date(item.properties.Day.date.start) }}</div>
				</div>
			</div> 
		</div>
	</div>
</template>

<script>

	import dateFormat from 'dateformat';

	export default {

		props: { data: { type: Object, default: () => ({}) } },

		methods:{
			date(date){
				if(new Date().getDate().toString() === dateFormat(date, "UTC:d")) return "Today"
				return dateFormat(date, "UTC:mmmm dS, yyyy");
			},
			getDate(date){
				return new Date().getDate().toString() === dateFormat(date, "UTC:d");
			}

			
		}
	}
</script>