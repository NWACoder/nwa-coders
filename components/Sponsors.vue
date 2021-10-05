<template>
	<div class="text-white py-12">
		<h2 class="text-center text-2xl pt-12 px-4">Proud Sponsors</h2>
    	<div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:px-8">
      		<div class="grid grid-cols-2 gap-8 md:grid-cols-6 lg:grid-cols-5">
				<div v-for="item in items" :key="item.name" class="col-span-1 flex justify-center md:col-span-2 lg:col-span-1">
					<img class="h-12" :src="item.img" alt="Tuple" />
				</div>
      		</div>
    	</div>
	</div>
</template>

<script>
	export default {
		data(){
			return{
				items: [
					{ name: "Item One", link: "/", img: "https://tailwindui.com/img/logos/tuple-logo-gray-400.svg" },
					{ name: "Item One", link: "/", img: "https://tailwindui.com/img/logos/tuple-logo-gray-400.svg" },
					{ name: "Item One", link: "/", img: "https://tailwindui.com/img/logos/tuple-logo-gray-400.svg" },
					{ name: "Item One", link: "/", img: "https://tailwindui.com/img/logos/tuple-logo-gray-400.svg" },
					{ name: "Item One", link: "/", img: "https://tailwindui.com/img/logos/tuple-logo-gray-400.svg" },
				],
			}
		},
	}
</script>