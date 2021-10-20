<template>
<!-- target a new window instead of opening this in the same window
	use svg img of hexagon 
	<a :target="aResource.properties.URL.rich_text[0].text.content" 
		class="relative border-8 border-white bg-gradient-to-b 
		from-green-600 to-green-900 rounded-lg
		h-full xl:h-80 opacity-95 hover:opacity-100 hover:border-gray-200">
		<div class=" rounded-lg p-4 w-auto cursor-pointer">
			<div class="text-center text-xl xl:text-2xl pb-6">
				<p class="text">{{ aResource.properties.Name.title[0].text.content }}</p> 
			</div>
			<div class="flex px-4 h-full text-center">
				<div class="text-center text-lg xl:text-xl">
					{{aResource.properties.Description.rich_text[0].text.content}}
				</div>
			</div>
		</div>
	</a> 
	-->
	<div>
		<!-- <img src="../../assets/img/hexagon.svg" alt="hexagonal shape with letter in it"
				 class="h-40">
        <p>{{ aResource.properties.Name.title[0].text.content[0] }}</p>
		<a :target="aResource.properties.URL.rich_text[0].text.content" class=" ">
			
			
		</a> -->
	</div>
</template>

<script>
	export default {
		props: ['aResource']
	}
</script>

<style>
	.margin-adjust:nth-child(even) {
        transform: translateX(65%);
    }
</style>