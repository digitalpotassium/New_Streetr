<script lang="ts">
	import Globe from '$lib/components/Globe.svelte';
</script>

<div class="min-h-screen w-full flex flex-col items-center justify-center bg-black text-white relative overflow-hidden selection:bg-white/20">
	<!-- Background Gradients for Depth -->
	<div class="absolute top-[-20%] left-[-10%] w-[500px] h-[500px] bg-blue-900/10 rounded-full blur-[120px] pointer-events-none"></div>
	<div class="absolute bottom-[-20%] right-[-10%] w-[500px] h-[500px] bg-purple-900/10 rounded-full blur-[120px] pointer-events-none"></div>

	<!-- Content Container -->
	<main class="z-10 flex flex-col items-center justify-center w-full max-w-4xl px-4 py-12 space-y-12">
		
		<!-- Logo Section -->
		<header class="animate-fade-in-up">
			<h1 class="text-6xl md:text-8xl font-black tracking-tighter bg-clip-text text-transparent bg-gradient-to-r from-blue-400 via-purple-500 via-pink-500 to-red-500 bg-[length:300%_auto] animate-gradient-flow drop-shadow-[0_0_25px_rgba(168,85,247,0.4)] pb-2">
				STREETR
			</h1>
		</header>

		<!-- Globe Section -->
		<div class="w-full relative animate-fade-in transition-transform duration-700 hover:scale-[1.02]">
             <!-- Subtle glow behind globe -->
             <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-[60%] h-[60%] bg-blue-500/5 rounded-full blur-[60px]"></div>
			<Globe />
		</div>

		<!-- Status Text Section -->
		<div class="text-center space-y-4 animate-fade-in-up" style="animation-delay: 200ms;">
			<p class="text-xl md:text-2xl font-light text-white/80 tracking-wide">
				The beta has concluded
			</p>
			<p class="text-sm md:text-base text-white/40 font-mono uppercase tracking-widest">
				Stay tuned for more
			</p>
		</div>

        <!-- Optional subtle footer line -->
        <div class="absolute bottom-8 w-full text-center">
            <div class="w-12 h-[1px] bg-white/10 mx-auto"></div>
        </div>

	</main>
</div>