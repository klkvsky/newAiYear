<script lang="ts">
	import '../app.css';
	//
	function randomIntFromInterval(min: number, max: number) {
		// min and max included
		return Math.floor(Math.random() * (max - min + 1) + min);
	}

	let rndInt: number = randomIntFromInterval(0, 391322);

	function updateRndInt() {
		rndInt = randomIntFromInterval(0, 391322);

		setTimeout(updateRndInt, 10000);
	}

	updateRndInt();
</script>

<main
	class="max-w-screen min-h-[90vh] max-h-fit bg-black text-white font-mono px-4 py-[10vh] overflow-hidden"
>
	<slot />
	<!-- {#key rndInt}
		<img
			src={`https://archillect.mhsattarian.workers.dev/${rndInt}/img`}
			alt=""
			class="fixed top-[2.5vh] left-[2vw] z-0 opacity-20 h-[85vh] w-[96vw] object-cover"
		/>
	{/key} -->
</main>
