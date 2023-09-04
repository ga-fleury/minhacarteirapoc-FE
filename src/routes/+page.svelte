<script>
	/** @type {number} */
	let apiResponse;

	async function roll() {
		const response = await fetch('https://q08tmqg247.execute-api.sa-east-1.amazonaws.com/dev/', {
            headers: {
                "Access-Control-Allow-Origin": '*',
                'Content-type': 'application/json'
            }
    });
		apiResponse = await response.json();
		console.log(apiResponse.message);
	}
</script>

<div class="flex flex-col justify-center items-center h-screen">
	<h1 class="text-3xl font-bold underline">Click button to make API request</h1>
	<button class="text-2xl bg-svelte-prime-900 py-2 px-6 rounded shadow text-black" on:click={roll}>
		Click Me
	</button>

	<p id="api-response">{apiResponse}</p>
</div>
