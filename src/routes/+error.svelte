<script>
	import { page } from '$app/stores';
  </script>
<div class="flex flex-col items-center justify-items-center place-content-center lg:justify-items-start  w-screen h-screen">
	<div class="">
		<h1 class="text-5xl text-center mb-4">{$page.status}</h1>
		<h3 class="text-3xl text-center ">{$page.error.message}</h3>
	</div>
	<br><br>
	<div class="">
		<p class="text-center text-2xl m-2"> Oops!</p>
		<p class="text-center">The top of the page should have info on why you are seeing this page</p>
	</div>
<!-- <div class="self-center">
    <img src="/images/hammerpot.png" alt="Logo" class="rounded-full w-1/5 m-4">
</div> -->
</div>