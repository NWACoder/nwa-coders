<template>
	<div class="text-white container mx-auto mt-12 px-4 md:px-0">
		<div class="aspect-w-16 aspect-h-9 mx-auto bg-gray-800" v-if="page.properties.Video.rich_text.length > 0">
			<iframe  id="ytplayer" type="text/html" class="h-full w-full" :src="'https://www.youtube.com/embed/'+page.properties.Video.rich_text[0].plain_text" frameborder="0" ></iframe>
		</div>
		
		<div class="bg-white text-black p-4 bg-opacity-90 rounded-b-3xl"> 
			
		<h6 class="text-center"><a href="/speakers">Speakers</a> / <span class="text-green-800">{{ page.properties.Name.title[0].plain_text }}</span></h6>
		<h1 class="text-center text-4xl mb-4 mt-12 uppercase">
			{{ page.properties.Topic.rich_text[0].plain_text }}
		</h1>
		<p class="text-center text-lg mb-12 uppercase ">Guest Speaker: {{ page.properties.Name.title[0].plain_text }}</p>
		<div class="block">
			<div class="border-b border-gray-200">
				<nav class="-mb-px flex space-x-8" aria-label="Tabs">
					<a v-for="(tab, index) in tabs" :key="tab.name" @click='selectTab(index)' :href="tab.href" :class="[tab.current ? 'border-green-200 text-green-600' : 'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300', 'whitespace-nowrap py-4 px-1 border-b-2 font-medium text-sm']" :aria-current="tab.current ? 'page' : undefined">{{ tab.name }}
					</a>
				</nav>
			</div>
		</div>
		<div class="my-4 leading-relaxed " v-if="tabs[0].current" v-html="content">
		</div>
		
		<div class="my-4" v-if="tabs[1].current">
			
		</div>
		</div> 

	</div>
</template>

<script>
	export default {

		async asyncData({ $axios, params }) {
			
			let page = {}
			let blocks = {}
			let content = ''

			const filterData = { 
				filter: { "and":  [ 
						{ property: "Slug", text: { equals: params.slug } }, 
						{ property: "Status", select: { equals: "Published" } }
					]
				}
			}
			
			page = await $axios.$post('databases/815035805b6d4a53ab7a74c81ee7fa0b/query', filterData)

			blocks = await $axios.$get(`blocks/${page.results[0].id}/children`)

			const childBlocks = await Promise.all(blocks.results.filter((block) => block.has_children)
				.map(async (block) => {
					const blocky = await $axios.$get(`blocks/${block.id}/children`)
					return {
						id: block.id,
						children: blocky.results
					} 
				})
			)
			
			const blocksWithChildren = blocks.results.map((block) => {
				if (block.has_children && !block[block.type].children) {
					block[block.type].children = childBlocks.find(
			        	(x) => x.id === block.id
			      	)?.children;
			    }
			    return block;
			})

			// build out content
			const renderBlocks = (block) => {

				const { type, id } = block;
  				const value = block[type];

				switch (type) {
					case 'paragraph':
						if(value.text.length === 1){
							let classList = 'leading-relaxed'
							let textContent = '<p>'
							value.text.forEach( text =>{
								if(text.annotations.bold){
									classList = 'font-bold'
									textContent += `<span class="${classList}">${text.plain_text}</span>`
								}else{
									textContent += `${text.plain_text}`
								}
							})
							return `${textContent}</p>`
						}else{
							return '<br>'
						}
					case 'numbered_list_item':
						return `<li class="leading-relaxed ml-6">${value.text[0].plain_text}</li>`
					case 'bulleted_list_item':{
						let classList = ''
						let textContent = '<li class="leading-relaxed ml-4">'
						value.text.forEach( text =>{
							if(text.annotations.bold){
								classList = 'font-bold'
								textContent += `<span class="${classList}">${text.plain_text}</span>`
							}else{
								textContent += `${text.plain_text}`
							}
						})
						return `${textContent}</li>`
					}
					case "to_do":
				    	return  `<label for=${id}><input type="checkbox" id=${id} defaultChecked=${value.checked} /> ${value.text}</label>`
					default:
    			}

			}

			blocksWithChildren.forEach( block =>{
				content += renderBlocks(block)
				if(block.has_children) block[block.type].children.forEach( (block, index,array) =>{ 
					if(block.type === 'numbered_list_item' && index === 0) content += `<ol class="list-decimal list-inside">`
					content += renderBlocks(block)
					if(block.type === 'numbered_list_item' && index === array.length -1) content += '</ol>'
					
				})

			})

			return { page: page.results[0], content }
		},

		data(){
			return {
				tabs: [
					  { name: 'Notes', href: '#', current: true },
					  { name: 'Resources', href: '#', current: false },
					],
			}
		},

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
		
		methods: {
			selectTab (i) {
				this.tabs.forEach((tab, index) => {
				tab.current = (index === i)
				})
			},
		},
	}
</script>
