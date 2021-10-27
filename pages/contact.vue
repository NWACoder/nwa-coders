<template>
	<div class="text-white container mx-auto mt-12 h-screen">

		<div>
			<h1 class="text-center text-4xl my-12 uppercase">Connect with us</h1>
		</div>
		<div class="grid grid-cols-1 lg:grid-cols-4 gap-0 lg:gap-8">
			<div class="grid grid-cols-4 lg:block w-full">
				<button v-for="item in contacts" :key="item"
					:class="{ 'border-green-800 bg-green-300 text-black': current.type == item.type }" 
					class=" lg:block w-full lg:w-full mb-12 border-r-0 lg:border-r-2 border-white hover:border-green-800 p-2 hover:bg-green-300 hover:text-black"
					@click="current.type = item.type; current.description = item.description" 
				>{{item.type}}</button>
			</div>
			<div class="col-span-3 p-4">
				<h2 class="text-2xl mb-4">{{ current.type }}</h2>
				<hr class="mb-4 border-gray-400">
				<p class="text-white mb-12">{{ current.description}}</p>
				<form class="kwes-form" action="https://kwesforms.com/api/foreign/forms/voIkktSRzfFTBxsZzrSn">
					
					<div class=" mb-6">
						<input type="text" name="name" placeholder="Full Name" rules="required|max:255" class="w-full shadow-lg p-2 block text-black">
					</div>
					
					<div class=" mb-6">
						<input type="text" name="email" placeholder="Email" rules="required|Email" class="w-full shadow-lg p-2 block text-black">
					</div>

					<div class="mb-6 text-black hidden">
						<input type="text" name="topic" placeholder="Topic" rules="max:255" class="w-full shadow-lg p-2 block text-black" v-model="current.type">
					</div>

					<div v-show="current.type == 'Business'" class=" mb-6">
						<input type="text" name="BusinessName" placeholder="Business Name" rules="max:255" class="w-full shadow-lg p-2 block">
					</div>

					<div class=" mb-6">
						<textarea name="message" rows="10" class="block w-full shadow-lg text-black" rules="required|max:255"></textarea>
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
			const contacts = [ { type: "General", description: "Send general inquiries" },
				{ type: "Sponsor", description: "intrested in sponsor and event or ..." },
				{ type: "Business", description: "Looking for developers or help with building out your businesss" },
				{ type: "Guest Speaker", description: "We are accepting any content creator who is intrested in giving a talk to our community" }];

			return{
				contacts,
				current: { type: "General", description: "Send general inquiries" }
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