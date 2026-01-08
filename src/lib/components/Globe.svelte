<script lang="ts">
	import { onMount } from 'svelte';
	import createGlobe from 'cobe';

	let canvas: HTMLCanvasElement;
	let phi = 0;

	onMount(() => {
		let width = 0;

		const onResize = () => {
             // Check if canvas exists to avoid errors on quick unmounts
             if (canvas) {
                 width = canvas.offsetWidth;
             }
        };
		window.addEventListener('resize', onResize);
		onResize();

		const globe = createGlobe(canvas, {
			devicePixelRatio: 2,
			width: width * 2,
			height: width * 2,
			phi: 0,
			theta: 0,
			dark: 1,
			diffuse: 1.2,
			mapSamples: 16000,
			mapBrightness: 6,
			baseColor: [0.3, 0.3, 0.3],
			markerColor: [0.1, 0.8, 1],
			glowColor: [0.1, 0.1, 0.1],
			markers: [
				// Example markers (optional)
				// { location: [37.7595, -122.4367], size: 0.03 },
				// { location: [40.7128, -74.006], size: 0.03 }
			],
			onRender: (state) => {
				// Called on every animation frame.
				// state.phi = phi
				state.phi = phi;
				phi += 0.005;
			}
		});

		return () => {
            globe.destroy();
            window.removeEventListener('resize', onResize);
        };
	});
</script>

<div class="relative flex w-full max-w-[600px] items-center justify-center aspect-square mx-auto">
	<canvas
		bind:this={canvas}
		style="width: 100%; height: 100%;"
        class="opacity-90 hover:opacity-100 transition-opacity duration-500"
	></canvas>
</div>
