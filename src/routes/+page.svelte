<script>
	let apiResponse = '';

	async function roll() {
		const response = await fetch('https://q08tmqg247.execute-api.sa-east-1.amazonaws.com/dev/', {
			headers: {
				'Access-Control-Allow-Origin': '*',
				'Content-type': 'application/json'
			}
		});
		apiResponse = await response.json();
		console.log(apiResponse);

		if (response.ok) {
			return apiResponse;
		} else {
			throw new Error(apiResponse);
		}
	}

	function handleClick() {
		apiResponse = roll();
	}
</script>

<div class="flex flex-col justify-center items-center h-screen gap-y-[50px]">
	<h1 class="text-3xl font-bold underline">Clique para fazer um request</h1>
	<button
		class="text-2xl py-2 px-6 rounded shadow text-white bg-svelte-prime"
		on:click={handleClick}
	>
		Beth?
	</button>
	{#if apiResponse != ''}
		{#await apiResponse}
			<p>...waiting</p>
		{:then body}
			<p>{body.message}</p>
		{:catch error}
			<p style="color: red">{error.message}</p>
		{/await}
	{/if}
</div>
