<script lang="ts">
	import Globe from '$lib/components/Globe.svelte';
</script>

<div
	class="relative flex min-h-screen w-full flex-col items-center justify-center overflow-hidden bg-black text-white selection:bg-white/20"
>
	<!-- Globe Background -->
	<Globe />

	<!-- Background Gradients for Depth -->
	<div
		class="pointer-events-none absolute left-[-10%] top-[-20%] h-[500px] w-[500px] rounded-full bg-blue-900/10 blur-[120px]"
	></div>
	<div
		class="pointer-events-none absolute bottom-[-20%] right-[-10%] h-[500px] w-[500px] rounded-full bg-purple-900/10 blur-[120px]"
	></div>

	<!-- Content Container -->
	<main
		class="z-10 flex w-full max-w-4xl flex-col items-center justify-center px-4 py-12 space-y-12"
	>
		<!-- Logo Section -->
		<header class="animate-fade-in-up">
			<h1
				class="bg-gradient-to-r from-blue-400 via-purple-500 via-pink-500 to-red-500 bg-[length:300%_auto] bg-clip-text pb-2 text-6xl font-black tracking-tighter text-transparent drop-shadow-[0_0_25px_rgba(168,85,247,0.4)] animate-gradient-flow md:text-8xl"
			>
				STREETR
			</h1>
		</header>

		<!-- Status Text Section -->
		<div class="animate-fade-in-up space-y-4 text-center" style="animation-delay: 200ms;">
			<p class="text-xl font-light tracking-wide text-white/80 md:text-2xl">
				The beta has concluded
			</p>
			<p class="font-mono text-sm uppercase tracking-widest text-white/40 md:text-base">
				Stay tuned for more
			</p>
		</div>

		<!-- Optional subtle footer line -->
		<div class="absolute bottom-8 w-full text-center">
			<div class="mx-auto h-[1px] w-12 bg-white/10"></div>
		</div>
	</main>
</div>
