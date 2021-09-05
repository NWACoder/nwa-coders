<template>
	<div class="container mx-auto grid grid-cols-2 py-4 px-4 md:px-0">
		<a href="/" class="p-4 sm:p-0 text-2xl"><span class="font-bold">NWA C</span>oders</a>
		<div class="cursor-pointer md:hidden justify-self-end hover:bg-black hover:text-white p-4" @click="toggle = !toggle">Menu</div>
		<div :class="{ 'hidden': toggle }" 
		class="col-span-2 md:col-span-1 place-self-center md:justify-self-end md:block space-x-8">
			<a v-for="item in nav" :key="item.name" :href="item.path"
			class="block md:inline-block "> {{ item.name }}</a>
			<a class="bg-black text-white px-5 py-3 text-sm shadow-sm font-medium tracking-wider" href="https://discord.gg/cjGQR9Rq8F" target="_blank">Discord Community </a>
		</div>
	</div>
</template>

<script>
	export default {
		data(){
			return{
				nav: [
					// { name: "Sponsor", path: "/sponsor" },
					// { name: "Events", path: "/events" },
					// { name: "Contact", path: "/contact" },
					// { name: "About", path: "/about" },
					// { name: "Resources", path: "/resources" }
				],
				toggle: true
			}
		},
	}
</script>