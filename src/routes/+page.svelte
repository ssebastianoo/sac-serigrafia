<script lang="ts">
	import screenPrintingVideo from '$lib/assets/screen-printing.mp4';
	// import screenPrinting from '$lib/assets/screen-printing.gif';
	import logo from '$lib/assets/logo.png';
	import { Menu, X } from '@lucide/svelte';

	let sideBar = $state<HTMLDivElement>();
</script>

<video
	autoplay
	muted
	loop
	playsinline
	id="myVideo"
	class="absolute top-0 left-0 -z-10 h-full w-full object-cover opacity-30"
>
	<source src={screenPrintingVideo} type="video/mp4" />
</video>

<div class="flex min-h-[calc(100dvh-5rem)] flex-col justify-between">
	<div class="sm:hidden">
		<button
			class="cursor-pointer"
			onclick={() => {
				sideBar?.animate?.(
					[
						{
							right: '100%'
						},
						{
							right: '0'
						}
					],
					{
						duration: 500,
						easing: 'cubic-bezier(.14,.66,.39,.96)',
						fill: 'forwards'
					}
				);
			}}
		>
			<Menu />
		</button>
	</div>
	<div
		bind:this={sideBar}
		class="absolute top-0 right-full z-10 flex h-dvh w-full flex-col items-center justify-center gap-12 rounded-md font-light backdrop-blur-lg sm:static sm:h-auto sm:w-full sm:flex-row sm:justify-end sm:gap-10 sm:backdrop-blur-none"
	>
		<button
			class="absolute top-10 right-10 cursor-pointer sm:hidden"
			onclick={() => {
				sideBar?.animate?.(
					[
						{
							right: '0'
						},
						{
							right: '100%'
						}
					],
					{
						duration: 500,
						easing: 'cubic-bezier(.14,.66,.39,.96)',
						fill: 'forwards'
					}
				);
			}}><X /></button
		>
		<a class="hover:underline" href="/">Home</a>
		<a class="hover:underline" href="/prodotti">Prodotti</a>
		<a class="hover:underline" href="/soluzioni">Soluzioni</a>
		<a class="hover:underline" href="/news">News</a>
		<a class="hover:underline" href="/storia">Storia</a>
		<a class="hover:underline" href="/contatti">Contatti</a>
	</div>
	<div>
		<div
			class="flex translate-y-20 animate-[slideUp_1s_ease-in-out_forwards_3.2s] flex-col items-center font-thin tracking-normal sm:mt-[104px]"
		>
			<div class="flex gap-[8px] text-4xl">
				<h1 class="animate-[fadeIn_.5s_ease-in-out_forwards_.2s] opacity-0">Dal</h1>
				<div class="relative h-[40px] w-[84px] overflow-hidden">
					<h1
						class="absolute right-full animate-[fromLeft_.5s_cubic-bezier(.14,.66,.39,.96)_forwards_1s] font-medium"
					>
						1966
					</h1>
					<div
						class="absolute bottom-[1px] h-[1px] w-0 animate-[full_.5s_cubic-bezier(.14,.66,.39,.96)_forwards_1.8s] bg-white"
					></div>
				</div>
			</div>
			<h1
				class="w-0 animate-[fullWord1Mobile_.5s_cubic-bezier(.14,.66,.39,.96)_forwards_2.3s] overflow-hidden text-3xl whitespace-nowrap sm:animate-[fullWord1_.5s_cubic-bezier(.14,.66,.39,.96)_forwards_2.3s] sm:text-4xl"
			>
				produciamo serigrafie
			</h1>
			<h1
				class="w-0 animate-[fullWord2Mobile_.5s_cubic-bezier(.14,.66,.39,.96)_forwards_2.8s] overflow-hidden text-3xl whitespace-nowrap sm:animate-[fullWord2_.5s_cubic-bezier(.14,.66,.39,.96)_forwards_2.8s] sm:text-4xl"
			>
				per le Aziende
			</h1>
		</div>
		<div
			class="mt-10 flex animate-[fadeIn_1s_ease-in-out_forwards_3.3s] flex-col items-center gap-1 text-xl opacity-0"
		>
			<a
				href="/catalogo"
				class="bg-primary-transparent hover:bg-primary rounded-md p-2 font-extralight transition-[background-color_0.5s_ease-in-out]"
				>Sfoglia il catalogo</a
			>
		</div>
	</div>
	<!-- <h1 class="text-5xl sm:text-7xl">SAC <br /> SERIGRAFIA</h1> -->
	<div class="flex justify-center sm:justify-start">
		<img src={logo} alt="Logo" class="w-52 sm:w-80" />
	</div>
</div>
