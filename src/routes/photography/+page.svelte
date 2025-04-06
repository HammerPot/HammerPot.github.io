<script lang="ts">
	import { onMount } from 'svelte';
	import Lazy from 'svelte-lazy';
	// import Image from '/images/showcase/flower.JPG?format=jpeg;webp&w=200;400;600;1200';
	
	// const imageGlob = import.meta.glob('/images/showcase/*.JPG', {
	// 	query: { format: 'jpeg;webp', w: '200;400;600;1200' },
	// 	import: 'default',
	// 	eager: true,
	// });
	// const videoGlob = import.meta.glob('/images/showcase/*.mov', { eager: true });

	// const imageUrls = Object.values(imageGlob);
	// const videoUrls = Object.values(videoGlob);
	// const mediaUrls = [...imageUrls, ...videoUrls];

	// console.log(imageGlob);
	// console.log(videoGlob);
	// console.log(imageUrls);
	// console.log(videoUrls);
	// console.log(mediaUrls);
	// console.log(Image);
	
	
	let media = [
		{image: "/images/showcase/flower2.JPG", alt: "A flower, again", text: "Flower TWO", type: "", height: 0, width: 0},
		{image: "/images/showcase/bee.JPG", alt: "A close up of a bee", text: "Bee", type: "", height: 0, width: 0},
		{image: "/images/showcase/flower.JPG", alt: "A flower", text: "Flower", type: "", height: 0, width: 0},
		{video: "/images/showcase/beemovie.mov", alt: "A video of a bee", text: "Bee Video", type: "", height: 0, width: 0},
		{image: "/images/showcase/beachpano.JPG", alt: "A panorama of a beach", text: "Beach Panorama", type: "panorama_landscape", height: 0, width: 0},
		{image: "/images/showcase/bridgepano.JPG", alt: "A panorama of a bridge", text: "Bridge Panorama", type: "panorama_portrait", height: 0, width: 0},
		{image: "/images/showcase/car.JPG", alt: "A car engine", text: "Car", type: "", height: 0, width: 0},
		{image: "/images/showcase/driver.JPG", alt: "A driver statue", text: "Driver Statue", type: "", height: 0, width: 0},
		{image: "/images/showcase/morningbeams.JPG", alt: "An intersection with the morning sun beaming brightly", text: "Intersection with LIGHT", type: "", height: 0, width: 0},
		{image: "/images/showcase/internals.JPG", alt: "The internal circuitry of an Exit Sign", text: "Exit Sign Internals", type: "", height: 0, width: 0},
		{image: "/images/showcase/lizard.JPG", alt: "A lizard in a tree", text: "Lizard", type: "", height: 0, width: 0},
		{image: "/images/showcase/morningscape.JPG", alt: "The morning sky", text: "Morning Sky", type: "", height: 0, width: 0},
		{image: "/images/showcase/mushhorz.JPG", alt: "A close up of mushrooms in landscape", text: "Mushrooms", type: "", height: 0, width: 0},
		{image: "/images/showcase/mushvert.JPG", alt: "A close up of mushrooms in portrait", text: "Mushrooms, again", type: "", height: 0, width: 0},
		{image: "/images/showcase/rainbowpano.JPG", alt: "A panorama with a rainbow", text: "Rainbow Panorama", type: "panorama_portrait", height: 0, width: 0},
		{image: "/images/showcase/shell.JPG", alt: "A shell in sand", text: "Shell", type: "", height: 0, width: 0},
		{image: "/images/showcase/squirrel.JPG", alt: "A squirrel", text: "Squirrel", type: "", height: 0, width: 0},
		{image: "/images/showcase/sunsolo.JPG", alt: "The sun behind a rooftop", text: "Sun Silhouette", type: "", height: 0, width: 0},
	]
	let media1 = []
	let loaded = false
	// console.log(media)
	// console.log(media.length)
	onMount(() => {
		media.forEach(item => {
			// console.log(loaded + " inside func")
			if (item.type != "panorama_landscape" && item.type != "panorama_portrait") {
				if (item.image) {
					const image = new Image();
					image.src = item.image;
					item.height = image.naturalHeight;
					item.width = image.naturalWidth;
					if (image.naturalHeight > image.naturalWidth) {
						item.type = "portrait";
						console.log("portrait " + item.height + "x" + item.width + " " + item.image)
					}
					else if (image.naturalWidth > image.naturalHeight) {
						item.type = "landscape";
						console.log("landscape " + item.height + "x" + item.width + " " + item.image)
					}
					else if (image.naturalWidth == image.naturalHeight) {
						item.type = "square";
						console.log("square " + item.height + "x" + item.width + " " + item.image)
					}
				} else if (item.video) {
					const video = document.createElement('video');
					video.src = item.video;
					video.addEventListener('loadedmetadata', () => {
						item.height = video.videoHeight;
						item.width = video.videoWidth;
						if (video.videoWidth > video.videoHeight) {
							item.type = "landscape";
							console.log("portrait " + item.height + "x" + item.width + " " + item.video)

						}
						else if (video.videoHeight > video.videoWidth) {
							item.type = "portrait";
							console.log("landscape " + item.height + "x" + item.width + " " + item.video)
						}
						else if (video.videoWidth == video.videoHeight) {
							item.type = "square";
							console.log("square " + item.height + "x" + item.width + " " + item.video)
						}
					})
				}
			}
			else {
				if (item.image){
					const image = new Image();
					image.src = item.image;
					item.height = image.naturalHeight;
					item.width = image.naturalWidth;
					console.log("pano " + item.height + "x" + item.width + " " + item.image)
				} else if (item.video) {
					const video = document.createElement('video');
					video.src = item.video;
					video.addEventListener('loadedmetadata', () => {
						item.height = video.videoHeight;
						item.width = video.videoWidth;
						console.log("pano " + item.height + "x" + item.width + " " + item.video)
						
					})
				}
			}
		})
		media1 = media
		console.log(loaded + " before switch")
		loaded = true
		console.log(loaded + " after switch")
	})

	// console.log(media1)

// console.log(loaded + " outside func")
</script>

<h1 class="text-5xl text-center mb-4 mt-4 pt-1">Photography</h1>

<div class="grid lg:grid-cols-3 md:grid-cols-2 grid-cols-1 grid-flow-row-dense gap-8 mb-4 p-4">
	<!-- {#each media as item}
		{#if item.image}
			{#if item.type == "panorama_landscape"}
			<div class="   p-12 col-span-2">
				  <h3 class=" rounded-t-lg mb-4 text-3xl text-center">{item.text}</h3>
				<img src={item.image} alt={item.alt} class=" rounded-lg ">
			</div>
			{:else if item.type == "panorama_portrait"}
			<div class="   p-12 row-span-3">
				  <h3 class=" rounded-t-lg mb-4 text-3xl text-center">{item.text}</h3>
				<img src={item.image} alt={item.alt} class=" rounded-lg ">
			</div>
			{:else}
			<div class="   p-12">
				  <h3 class=" rounded-t-lg mb-4 text-3xl text-center">{item.text}</h3>
				<img src={item.image} alt={item.alt} class=" rounded-lg">
			</div>
			{/if}
		{:else if item.video}
			<div class="   p-12">
				  <h3 class=" rounded-t-lg mb-4 text-3xl text-center">{item.text}</h3>
				<video src={item.video} aria-label={item.alt} class=" rounded-lg" autoplay loop muted playsinline disablepictureinpicture disableremoteplayback ></video>
			</div>
		{:else}
			<p class="text-color-white">Invalid media type!</p>
		{/if} 
	{/each} -->


{#if loaded}
<!-- {console.log(loaded + " inside if")} -->
	{#each media1 as item}
			<!-- {console.log(item)} -->
		{#if item.type == "panorama_landscape"}
			<div class="   p-12 lg:col-span-3 md:col-span-2 col-span-1" id={item.type}>
				<h3 class=" rounded-t-lg mb-4 lg:text-3xl md:text-xl text-l text-center">{item.text}</h3>
				{#if item.image}
					<Lazy keep={true} height={item.height}>
						<img src={item.image} alt={item.alt} class=" rounded-lg" id={item.type + " " + item.height}>
					</Lazy>
				{:else if item.video}
					<Lazy keep={true} height={item.height}>
						<video src={item.video} aria-label={item.alt} class=" rounded-lg" autoplay loop muted playsinline disablepictureinpicture disableremoteplayback ></video>
					</Lazy>
					{/if}
			</div>
		{:else if item.type == "panorama_portrait"}
			<div class="   p-12 row-span-3 " id={item.type}>
				<h3 class=" rounded-t-lg mb-4 lg:text-3xl md:text-xl text-l text-center">{item.text}</h3>
				{#if item.image}
					<Lazy keep={true} height={item.height}>
						<img src={item.image} alt={item.alt} class=" rounded-lg" id={item.type + " " + item.height}>
					</Lazy>
				{:else if item.video}
					<Lazy keep={true} height={item.height}>
						<video src={item.video} aria-label={item.alt} class=" rounded-lg" autoplay loop muted playsinline disablepictureinpicture disableremoteplayback ></video>
					</Lazy>
					{/if}
			</div>
		{:else if item.type == "landscape"}
			<div class="   p-12 lg:col-span-2 md:col-span-2 col-span-1" id={item.type}>
				<h3 class=" rounded-t-lg mb-4 lg:text-3xl md:text-xl text-l text-center">{item.text}</h3>
				{#if item.image}
					<Lazy keep={true} height={item.height}>
						<img src={item.image} alt={item.alt} class=" rounded-lg" id={item.type + " " + item.height}>
					</Lazy>
				{:else if item.video}
					<Lazy keep={true} height={item.height}>
						<video src={item.video} aria-label={item.alt} class=" rounded-lg" autoplay loop muted playsinline disablepictureinpicture disableremoteplayback ></video>
					</Lazy>
					{/if}
			</div>
		{:else if item.type == "portrait"}
			<div class=" flex flex-col justify-center   p-12 row-span-2" id={item.type}>
				<h3 class=" rounded-t-lg mb-4 lg:text-3xl md:text-xl text-l text-center">{item.text}</h3>
				{#if item.image}
					<Lazy keep={true} height={item.height}>
						<img src={item.image} alt={item.alt} class=" rounded-lg" id={item.type + " " + item.height}>
					</Lazy>
				{:else if item.video}
					<Lazy keep={true} height={item.height}>
						<video src={item.video} aria-label={item.alt} class=" rounded-lg" autoplay loop muted playsinline disablepictureinpicture disableremoteplayback ></video>
					</Lazy>
					{/if}
			</div>
		{:else if item.type == "square"}
			<div class="   p-12 row-span-1 col-span-1 " id={item.type}>
				<h3 class=" rounded-t-lg mb-4 lg:text-3xl md:text-xl text-l text-center">{item.text}</h3>
				{#if item.image}
					<Lazy keep={true} height={item.height}>
						<img src={item.image} alt={item.alt} class=" rounded-lg" id={item.type + " " + item.height}>
					</Lazy>
				{:else if item.video}
					<Lazy keep={true} height={item.height}>
						<video src={item.video} aria-label={item.alt} class=" rounded-lg" autoplay loop muted playsinline disablepictureinpicture disableremoteplayback ></video>
					</Lazy>
					{/if}
			</div>
		{:else}
			<div class="   p-12 " id={item.type}>
				<h3 class=" rounded-t-lg mb-4 lg:text-3xl md:text-xl text-l text-center">{item.text}</h3>
				{#if item.image}
					<Lazy keep={true} height={item.height}>
						<img src={item.image} alt={item.alt} class=" rounded-lg" id={item.type + " " + item.height}>
					</Lazy>
				{:else if item.video}
					<Lazy keep={true} height={item.height}>
						<video src={item.video} aria-label={item.alt} class=" rounded-lg" autoplay loop muted playsinline disablepictureinpicture disableremoteplayback ></video>
					</Lazy>
					{/if}
			</div>
		{/if}
	{/each}
{/if}
</div>