<template>
	<div class="text-white py-8">
		<div class="container mx-auto px-4 md:px-0 py-4 grid md:grid-cols-2 items-center">
			<div class="text-center md:text-left">
				<p class="text-sm">Upcoming</p>
				<p class="text-2xl">Events</p>
			</div>
			<div class="text-center md:justify-self-end p-2 rounded-lg space-x-4 text-black text-sm text-white">
				* All Virtual Events Hosted on Community Discord
				<!-- <label for="all" class="cursor-pointer ">
					<input id="all" type="radio" name="type" value="all" checked  >
					All
				</label>
				<label for="Virtual" class="cursor-pointer ">
					<input id="Virtual" type="radio" name="type" value="Virtual">
					Virtual
				</label>
				<label for="in-Person" class="cursor-pointer ">
					<input id="in-Person" type="radio" name="type" value="in-Person">
					in Person
				</label> -->
			</div>
		</div>

		<div class="container mx-auto px-4 md:px-0 my-8 grid grid-cols-2 lg:grid-cols-4 xl:grid-cols-5 gap-4 md:gap-12 ">
			<EventCard v-for="(item,index) in data" :item="item" :key="index"/>
		</div>
	</div>
</template>


<script>
	export default {

		props: { data: [] },

	}
</script>