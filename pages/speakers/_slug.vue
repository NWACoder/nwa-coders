<template>
	<div class="container mx-auto mt-12">

		<div class="aspect-w-16 aspect-h-9 mx-auto bg-gray-800">
				<iframe v-if="page.properties.Video.rich_text.length > 0"  id="ytplayer" type="text/html" class="h-full w-full"
  :src="'https://www.youtube.com/embed/'+page.properties.Video.rich_text[0].plain_text"
  frameborder="0" ></iframe>
			
		</div>
		
		<h1 class="text-center text-4xl mb-4 mt-12 uppercase">
			{{ page.properties.Topic.rich_text[0].plain_text }}
		</h1>
		<p class="text-center text-lg mb-12 uppercase ">Guest Speaker: {{ page.properties.Name.title[0].plain_text }}</p>
		<div class="block">
			<div class="border-b border-gray-200">
				<nav class="-mb-px flex space-x-8" aria-label="Tabs">
					<a v-for="(tab, index) in tabs" :key="tab.name" @click='selectTab(index)' :href="tab.href" :class="[tab.current ? 'border-indigo-500 text-indigo-600' : 'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300', 'whitespace-nowrap py-4 px-1 border-b-2 font-medium text-sm']" :aria-current="tab.current ? 'page' : undefined">{{ tab.name }}
					</a>
				</nav>
			</div>
		</div>
		<div class="my-4" v-if="tabs[0].current">
			<template v-for="item in content"  class="leading-relaxed">
				
				<p :key="item.id" v-if="item.type == 'paragraph' && item.paragraph.text.length == 1"
				:class="{ 'font-bold': item.paragraph.text[0].annotations.bold }"
				class="leading-relaxed">

					{{ item.paragraph.text[0].plain_text }}
				</p>

				<br v-else-if="item.type == 'paragraph' && item.paragraph.text.length == 0" :key="item.id" />
					
				<li :key="item.id" v-if="item.type == 'bulleted_list_item'"
				class="pl-4 leading-relaxed">
					{{ item.bulleted_list_item.text[0].plain_text }}
				</li>

			</template>	
		</div>
		
		<div class="my-4" v-if="tabs[1].current">
			
		</div>
	</div>
</template>

<script>
	export default {

		head(){
			return {
				title: this.page.properties.Topic.rich_text[0].plain_text,
				meta: [
				      {
				        property: 'og:title',
				        content: `#${this.page ? this.page.properties.Topic.rich_text[0].plain_text : ''}`,
				        vmid: 'og:title'
				      },
				      {
				        property: 'og:image',
				        content: `${this.page ? this.page.properties.Image.url : ''}`,
				        vmid: 'og:image'
				      },
				      {
				        property: 'og:description',
				        content: `${this.page ? `Guest Speaker: ${this.page.properties.Name.title[0].plain_text} ${this.page.properties.Topic.rich_text[0].plain_text}` : ''}`,
				        vmid: 'og:description'
				      },
				      {
				        property: 'twitter:title',
				        content: `${this.page ? this.page.properties.Topic.rich_text[0].plain_text : ''}`,
				        vmid: 'twitter:title'
				      },
				      {
				        property: 'twitter:image',
				        content: `${this.page ? this.page.properties.Image.url : ''}`,
				        vmid: 'twitter:image'
				      },
				      {
				        property: 'twitter:description',
				        content: `${this.page ? `Guest Speaker: ${this.page.properties.Name.title[0].plain_text} ${this.page.properties.Topic.rich_text[0].plain_text}` : ''}`,
				        vmid: 'twitter:description'
				      },
				      {
				        name: 'twitter:card',
				        content: `summary_large_image`,
				        vmid: 'twitter:card'
				      }
				    ]
			}
		},

		async asyncData({ $axios, params }) {
			
			let content = {}
			let page = {}

			const filterData = { 
				filter: { "and":  [ 
						{ property: "Slug", text: { equals: params.slug } }, 
						{ property: "Status", select: { equals: "Published" } }
					]
				}

			}
			
			page = await $axios.$post('databases/815035805b6d4a53ab7a74c81ee7fa0b/query', filterData)

			content = await $axios.$get(`blocks/${page.results[0].id}/children`)
		
			return { page: page.results[0], content: content.results }
		},
		data(){
			return {
				tabs: [
					  { name: 'Notes', href: '#', current: true },
					  { name: 'Resources', href: '#', current: false },
					]
			}
		},

		methods: {
			selectTab (i) {
				this.tabs.forEach((tab, index) => {
				tab.current = (index === i)
				})
			}
		},
	}
</script>
