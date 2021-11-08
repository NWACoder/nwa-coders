<template>
	<div class="col-span-1 flex flex-col text-center bg-white rounded-lg shadow divide-y divide-gray-200">
		<div class="flex-1 flex flex-col p-8">
			<img class="w-32 h-32 flex-shrink-0 mx-auto rounded-full" :src="speaker.properties.Image.files[0].file.url" alt="" />
			<h3 class="mt-6 text-gray-900 text-sm font-medium"> {{speaker.properties.Name.title[0].plain_text}}</h3>
			<dl class="mt-1 flex-grow flex flex-col justify-between">
				<dt class="sr-only">Title</dt>
				<dd class="text-gray-500 text-sm">{{ speaker.properties.Role.rich_text[0].plain_text }}</dd>
				<dt class="sr-only">Topic</dt>
				<dd class="mt-3 text-gray-500">
					<a :href="'/speakers/'+speaker.properties.Slug.rich_text[0].plain_text">{{ speaker.properties.Topic.rich_text[0].plain_text }}</a>
				</dd>
			</dl>
		</div>

	</div>
</template>

<script>
	export default{
		props: ['speaker']
	}
</script>