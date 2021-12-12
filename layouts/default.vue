<template>
	<div class="font-montserrat">
		<Notification>
			<p class="text-right text-lg font-bold">
				<span class="inline-flex relative h-3 w-3">
					<span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-red-400 opacity-75"></span>
					<span class="relative inline-flex rounded-full h-3 w-3 bg-red-500"></span>
				</span> <a href="https://www.youtube.com/channel/UCyDWpTnmcfi70tPmx5M1D4A/live" class="text-gray-800" target="_blank">we are live</a></p>
		</Notification>
		<Navigation/>
		<Nuxt />
		<Foot/>
	</div>
</template>
<style>
	body{
		@apply bg-gradient-to-b from-main via-mid to-second
	}
</style>