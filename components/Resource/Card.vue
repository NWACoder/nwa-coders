<template>
	<a :href="aResource.properties.URL.rich_text[0].text.content">
		<div class="relative border-8 border-white bg-green-600 rounded-lg p-4 h-auto xl:h-96 w-auto cursor-pointer">
			<div class="text-center text-xl xl:text-2xl">
				<p>{{ aResource.properties.Name.title[0].text.content }}</p> 
			</div>
			<div class="flex px-4 h-full text-center">
				<div class="text-center text-lg xl:text-2xl self-center">
					{{aResource.properties.Description.rich_text[0].text.content}}
				</div>
			</div>
		</div>
	</a>
</template>

<script>
	export default {
		props: ['aResource']
	}
</script>