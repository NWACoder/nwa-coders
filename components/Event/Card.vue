<template>
	<div 
	:class="'bg-'+item.properties.Type.select.color+'-600'"
	class="relative border-8 border-white rounded-lg p-4 h-96 w-auto cursor-pointer ">
	<a :href="item.properties.Link.url" target="_blank" class="absolute h-full w-full z-10"> </a>
		<!-- day -->
		<div class="absolute -right-4 -top-4 bg-white text-black rounded-full p-4 h-12 w-12  flex items-center justify-center text-sm text-center">
			{{ day(item.properties.Day.date.start) }}
		</div>
		<!-- month -->
		<div>
			{{ month(item.properties.Day.date.start) }}
		</div>
		<!-- title -->
		<div class="flex justify-center items-center px-4 h-72">
			<div class="text-center text-lg xl:text-xl">
				{{item.properties.Name.title[0].plain_text}}
				<p v-if="item.properties.Speaker.relation.length > 0" class="text-sm pt-4">Guest Speaker<br>{{ item.Speaker.children.properties.Name.title[0].plain_text }}</p>
			</div>
		</div>
		<!-- time -->
		<div class="absolute left-0 bottom-2 w-full text-sm xl:text-base ">
			<p class="text-center">Location: {{item.properties.Type.select.name}} </p>
			<p class="text-center">{{item.properties.Time.rich_text[0].plain_text}} CST</p>
		</div>

	</div>
</template>

<script>
	import dateFormat from 'dateformat';

	export default {

		props: { item: { type: Object, default: () => ({}) } },


		methods:{
			date(date){
				if(new Date().getDate().toString() === dateFormat(date, "UTC:d")) return "Today"
				return dateFormat(date, "UTC:mmmm dS, yyyy");
			},
			month(date){
				return dateFormat(date, "UTC:mmm");
			},
			day(date){
				return dateFormat(date, "UTC:d");
			},
			getDate(date){
				return new Date().getDate().toString() === dateFormat(date, "UTC:d");
			}
		}
		
	}
</script>