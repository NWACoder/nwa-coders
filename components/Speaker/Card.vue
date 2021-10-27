<template>
    <div class="relative rounded-lg border border-gray-300 bg-white px-6 py-5 shadow-sm flex items-center space-x-3 hover:border-gray-400 focus-within:ring-2 focus-within:ring-offset-2 focus-within:ring-green-500">
      
      <div class="flex-shrink-0">
        <img class="h-10 w-10 rounded-full" :src="speaker.properties.Image.url" alt="" />
      </div>
      <div class="flex-1 min-w-0">
      	<a :href="'/speakers/'+speaker.properties.Slug.rich_text[0].plain_text"  class="focus:outline-none">
          <span class="absolute inset-0" aria-hidden="true" />
          
          <p>{{ speaker.properties.Topic.rich_text[0].plain_text }}</p>
          <p class="text-sm font-medium text-gray-900">
            {{speaker.properties.Name.title[0].plain_text}}
          </p>
          <p class="text-sm text-gray-500 truncate">
            {{ speaker.properties.Role.rich_text[0].plain_text }}
          </p>
        </a>
      </div>

    </div>

</template>

<script>
	export default{
		props: ['speaker']
	}
</script>