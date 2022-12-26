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
</script>

<h1 class="font-bold text-4xl text-center">New Year Resolutions Ai Edition</h1>
<input
	type="text"
	class="bg-transparent border border-black dark:border-white rounded-full px-[30px] py-[15px] w-full font-medium text-lg"
	placeholder="От кого пожелание?"
/>
<button
	class="border border-black dark:border-white rounded-full px-[30px] py-[15px] w-full font-medium text-lg"
	on:click={() => {
		onSubmit();
	}}
>
	Узнать
</button>

{#if result}
	<p class="text-center">{result}</p>
{/if}
