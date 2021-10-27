<template>
	<div>
		<div class="sm:hidden md:flex">
			<img src="../../assets/img/hexCard.svg" alt="Image of a hexagon shape, with the titles first letter in it"
				class="h-40 w-full">
        	<h1 class="absolute card-letter font-bold ">{{ aResource.properties.Name.title[0].text.content[0] }}</h1>
			<div class="grid grid-cols-1 absolute text-center h-full title-description text-xl font-bold">
				<!-- Colorize the first letter of the title -->
				<h2 ref="descriptionTitle" class="h-5">
					<span class="text-green-600 font-bold">{{ aResource.properties.Name.title[0].text.content.slice(0, 1) }}</span>{{ aResource.properties.Name.title[0].text.content.slice(1, aResource.properties.Name.title[0].text.content.length) }}
				</h2>
				<p class="h-full self-auto text-lg font-normal">
					{{ aResource.properties.Description.rich_text[0].text.content }}
				</p>
			</div>	
		</div>
	</div>
</template>

<script>
	export default {
		props: ['aResource'],

		methods: {
			
		}
	}
</script>

<style>
	.card-letter {
		width: 13.5%;
		height: 100%;
		bottom: 0;
		text-align: center;
		padding-top: 0.15%;
		font-size: 6.5rem;
		padding-right: 3%;
	}

	.title-description {
		padding-left: 11%;
		width: 79%;
	}
</style>