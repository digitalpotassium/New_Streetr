<script lang="ts">
	import { onMount, tick } from 'svelte';
	import createGlobe from 'cobe';

	let canvas: HTMLCanvasElement;
	let phi = 0;
	let width = 0;

	onMount(() => {
		let globe: { destroy: () => void } | undefined;
		let resizeTimeout: NodeJS.Timeout;

		const initGlobe = async () => {
			if (!canvas) return;

			// Ensure width is set in DOM before creating globe
			const size = Math.max(window.innerWidth, window.innerHeight) * 1.3;
			width = size;
			await tick();

			if (globe) {
				globe.destroy();
			}

			let lastTime = performance.now();

			globe = createGlobe(canvas, {
				devicePixelRatio: Math.min(window.devicePixelRatio, 2),
				width: size * 2,
				height: size * 2,
				phi: 0,
				theta: 0.3, // Tilt it slightly for better look
				dark: 1,
				diffuse: 1.2,
				mapSamples: 12000,
				mapBrightness: 8, // Increased brightness
				baseColor: [0.4, 0.4, 0.4], // Slightly brighter base
				markerColor: [0.1, 0.8, 1],
				glowColor: [0.2, 0.2, 0.2], // Brighter glow
				markers: [],
				onRender: (state) => {
					const now = performance.now();
					const delta = now - lastTime;
					lastTime = now;
					state.phi = phi;
					phi += 0.0001 * delta;
				}
			});
		};

		const onResize = () => {
			// Debounce resize to prevent flashing/performance issues
			clearTimeout(resizeTimeout);
			resizeTimeout = setTimeout(initGlobe, 100);
		};

		window.addEventListener('resize', onResize);

		// Initial load
		initGlobe();

		return () => {
			if (globe) globe.destroy();
			window.removeEventListener('resize', onResize);
			clearTimeout(resizeTimeout);
		};
	});
</script>

<div class="fixed inset-0 z-0 flex items-center justify-center overflow-hidden pointer-events-none">
	<canvas
		bind:this={canvas}
		style="width: {width}px; height: {width}px; max-width: none;"
		class="opacity-40 transition-opacity duration-1000 ease-in-out"
	></canvas>
</div>
