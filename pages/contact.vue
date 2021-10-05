<template>
	<div class="text-white container mx-auto mt-12">

		<div>
			<h1 class="text-center text-4xl my-12 uppercase">Connect with us</h1>
		</div>
		<div class=" grid grid-cols-4 gap-8">
			<div class="block">
				<button v-for="item in contacts" :key="item"
					:class="{ 'border-blue-800': type == item }" 
					class="block w-full mb-12 border-r-2 border-white p-2 hover:bg-gray-300 hover:text-black"
					@click="type = item" 
				>{{item}}</button>
			</div>
			<div class="col-span-3">
				<h2 class="text-2xl mb-4">{{ type }}</h2>
				<hr class="mb-12 border-gray-600">
				<form class="kwes-form" action="https://kwesforms.com/api/foreign/forms/voIkktSRzfFTBxsZzrSn">
					
					<div class=" mb-6">
						<input type="text" name="name" placeholder="Full Name" rules="required|max:255" class="w-full shadow-lg p-2 block">
					</div>
					
					<div class=" mb-6">
						<input type="text" name="email" placeholder="Email" rules="required|Email" class="w-full shadow-lg p-2 block">
					</div>

					<div v-show="type == 'Guest Speaker'" class=" mb-6">
						<input type="text" name="topic" placeholder="Topic" rules="max:255" class="w-full shadow-lg p-2 block">
					</div>

					<div class=" mb-6">
						<textarea name="message" rows="10" class="block w-full shadow-lg" rules="required|max:255"></textarea>
					</div>

					<button type="submit" class="inline-flex items-center px-4 py-2 border border-gray-300 shadow-sm text-base font-medium rounded-md text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">Send</button>
				</form>
			</div>
		</div>
	</div>
</template>

<script>

	import kwesforms from 'kwesforms';

	export default {
		data(){
			return{
				contacts: [ "General", "Sponsor", "Business", "Guest Speaker"],
				type: "General"
			}
		},
		mounted(){
			kwesforms.init();
			if(this.$route.query.type) this.type = this.$route.query.type
			
		},
	}

</script>

<style>
	.kw-alert{
		display: none!important;
	}
	/*.kw-field-error-message{
		display:  none!important;
	}*/
</style>