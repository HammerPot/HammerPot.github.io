<script lang="ts">
	const media = [
		{image: "/images/showcase/flower2.jpeg", alt: "A flower, again", text: "Flower TWO", type: ""},
		{image: "/images/showcase/bee.JPG", alt: "A close up of a bee", text: "Bee", type: ""},
		{image: "/images/showcase/flower.jpeg", alt: "A flower", text: "Flower", type: ""},
		{image: "/images/showcase/beachpano.JPG", alt: "A panorama of a beach", text: "Beach Panorama", type: "panorama_landscape"},
		{image: "/images/showcase/bridgepano.JPG", alt: "A panorama of a bridge", text: "Bridge Panorama", type: "panorama_portrait"},
		{image: "/images/showcase/car.JPG", alt: "A car engine", text: "Car", type: ""},
		{image: "/images/showcase/driver.JPG", alt: "A driver statue", text: "Driver Statue", type: ""},
		{video: "/images/showcase/beemovie.mov", alt: "A video of a bee", text: "Bee Video", type: ""},
		{image: "/images/showcase/internals.JPG", alt: "The internal circuitry of an Exit Sign", text: "Exit Sign Internals", type: ""},
		{image: "/images/showcase/lizard.JPG", alt: "A lizard in a tree", text: "Lizard", type: ""},
		{image: "/images/showcase/morningbeams.JPG", alt: "An intersection with the morning sun beaming brightly", text: "Intersection with LIGHT", type: ""},
		{image: "/images/showcase/morningscape.JPG", alt: "The morning sky", text: "Morning Sky", type: ""},
		{image: "/images/showcase/mushhorz.JPG", alt: "A close up of mushrooms in landscape", text: "Mushrooms", type: ""},
		{image: "/images/showcase/mushvert.JPG", alt: "A close up of mushrooms in portrait", text: "Mushrooms, again", type: ""},
		{image: "/images/showcase/rainbowpano.JPG", alt: "A panorama with a rainbow", text: "Rainbow Panorama", type: "panorama_portrait"},
		{image: "/images/showcase/shell.JPG", alt: "A shell in sand", text: "Shell", type: ""},
		{image: "/images/showcase/squirrel.JPG", alt: "A squirrel", text: "Squirrel", type: ""},
		{image: "/images/showcase/sunsolo.jpeg", alt: "The sun behind a rooftop", text: "Sun Silhouette", type: ""}
	]
		media.forEach(item => {
			if (item.image) {
				// const image = new Image();
				// image.src = item.image;
				// if (image.naturalHeight > image.naturalWidth) {
				// 	item.type = "portrait";
				// }
				// else if (image.naturalWidth > image.naturalHeight) {
				// 	item.type = "landscape";
				// }
			} else if (item.video) {
				// const video = document.createElement('video');
				// video.src = item.video;
				// if (video.videoWidth > video.videoHeight) {
				// 	item.type = "landscape";

				// }
				// else if (video.videoHeight > video.videoWidth) {
				// 	item.type = "portrait";
				// }
			}
		})

</script>

<h1 class="text-5xl text-center m-4 pt-1">Photography</h1>

<div class="grid grid-cols-3 grid-flow-row-dense gap-4 m-4 p-4">
	{#each media as item}
		{#if item.image}
			{#if item.type == "panorama_landscape"}
			<div class="self-center col-span-2">
				<h3 class="text-3xl text-center">{item.text}</h3>
				<img src={item.image} alt={item.alt} class="rounded-lg ">
			</div>
			{:else if item.type == "panorama_portrait"}
			<div class="self-center row-span-3">
				<h3 class="text-3xl text-center">{item.text}</h3>
				<img src={item.image} alt={item.alt} class="rounded-lg ">
			</div>
			{:else}
			<div class="self-center">
				<h3 class="text-3xl text-center">{item.text}</h3>
				<img src={item.image} alt={item.alt} class="rounded-lg">
			</div>
			{/if}
		{:else if item.video}
			<div class="self-center">
				<h3 class="text-3xl text-center">{item.text}</h3>
				<video src={item.video} aria-label={item.alt} class="rounded-lg" autoplay loop muted></video>
			</div>
		{:else}
			<p class="text-color-white">Invalid media type!</p>
		{/if} 
	{/each}
</div>