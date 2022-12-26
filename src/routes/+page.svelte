<script>
	// @ts-nocheck
	import { Configuration, OpenAIApi } from 'openai';
	//
	const configuration = new Configuration({
		apiKey: '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'
	});
	const openai = new OpenAIApi(configuration);
	//

	async function apiRequest(input) {
		const completion = await openai.createCompletion({
			model: 'text-davinci-002',
			prompt: generatePrompt(input),
			temperature: 1,
			max_tokens: 100
		});
		result = completion.data.choices[0].text;
	}

	function generatePrompt(animal) {
		const capitalizedAnimal = animal;
		return `write a text in style of ${capitalizedAnimal}'s lyrics about new 2023 year resolution, make it in twitter post length and also make it rhyme in style of ${capitalizedAnimal}'s lyrics`;
	}
	//
	//
	//
	let animalInput = '';
	let result = '';

	async function onSubmit() {
		apiRequest(animalInput);
		animalInput = '';
	}

	//

	function randomIntFromInterval(min, max) {
		// min and max included
		return Math.floor(Math.random() * (max - min + 1) + min);
	}

	let rndInt = randomIntFromInterval(0, 391322);

	function updateRndInt() {
		rndInt = randomIntFromInterval(0, 391322);

		setTimeout(updateRndInt, 10000);
	}

	updateRndInt();
</script>

<div class="flex flex-col items-center gap-[30px] relative z-10">
	<div class="grid grid-cols-3 -mb-7">
		<div
			class="w-[28vw] bg-white/30 backdrop-blur-md relative z-10 bg-clip-content aspect-square rounded-full object-cover"
		/>
		<h1 class="font-bold text-4xl text-right relative z-10 col-span-2 -translate-y-4">
			New AI Year Resolution
		</h1>
	</div>

	<div class="flex flex-row items-center gap-[10px] w-full ">
		<!-- <img
			src={`https://archillect.mhsattarian.workers.dev/${rndInt}/img`}
			alt=""
			class="w-screen h-screen aspect-square fixed top-0 left-0 z-0 rounded-full object-cover opacity-50 rounded-b-none"
		/> -->
		<img
			src={`https://archillect.mhsattarian.workers.dev/${rndInt}/img`}
			alt=""
			class="w-screen h-screen aspect-square fixed top-0 left-0 z-0 rounded-full object-cover opacity-20 rounded-b-none"
		/>
		<div
			class="w-2/6 bg-white/20 backdrop-blur-md relative z-10 bg-clip-content aspect-square rounded-full object-cover animate-pulse"
		/>
		<div
			class="w-2/6 bg-white/10 backdrop-blur-md relative z-10 bg-clip-content aspect-square rounded-full object-cover"
		/>
		<div
			class="w-2/6 bg-white/30 backdrop-blur-md relative z-10 bg-clip-content aspect-square rounded-full object-cover"
		/>
		<!-- <img
			src={`https://archillect.mhsattarian.workers.dev/${rndInt}/img`}
			alt=""
			class="w-2/6 aspect-square rounded-full object-cover"
		/>
		<img
			src={`https://archillect.mhsattarian.workers.dev/${rndInt}/img`}
			alt=""
			class="w-2/6 aspect-square rounded-full object-cover"
		/> -->
	</div>
	<input
		type="text"
		class="bg-white/10 backdrop-blur-md  rounded-full px-[30px] py-[15px] w-full font-medium text-lg relative z-10 placeholder:text-white"
		placeholder="От кого пожелание?"
	/>
	<button
		class=" rounded-full px-[30px] py-[15px] w-full font-medium text-lg relative z-10 bg-white/10 backdrop-blur-md"
		on:click={() => {
			onSubmit();
		}}
	>
		Узнать
	</button>
	{#if result}
		<p class="text-center relative z-10">{result}</p>
	{/if}
</div>
