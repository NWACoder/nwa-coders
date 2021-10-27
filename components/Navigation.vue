<template>
	<div class="text-white container mx-auto grid grid-flow-col gap-4 py-4 px-4 md:px-0 relative">
		<a href="/" class="p-4 sm:p-0 text-2xl z-20"><span class="font-bold text-trim">NWA C</span>oders</a>
		<div class="cursor-pointer md:hidden justify-self-end  p-4 z-20" @click="toggle = !toggle">
			<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" /></svg>
		</div>
		<div :class="{ 'hidden': toggle }" 
		class="col-span-2 md:col-span-1 place-self-center md:justify-self-end md:block md:space-x-8 space-y-4 md:space-y-0 text-center md:text-right absolute md:relative h-screen md:h-auto bg-black md:bg-transparent w-full z-10 left-0 top-0 pt-24 md:pt-0

		">
			<a v-for="item in nav" :key="item.name" :href="item.path"
			class="block md:inline-block pb-2"> {{ item.name }}</a>
			<a class="block md:inline-block w-max mx-auto hover:border-2 hover:border-gray-700 bg-white text-black rounded-md px-5 py-3 text-sm shadow-sm font-medium tracking-wider" href="https://discord.gg/bDFe9F8mXD" target="_blank">Discord Community </a>
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
					// { name: "Resources", path: "/resources" },
					// { name: "About", path: "/about" },
				],
				toggle: true
			}
		},
	}
</script>