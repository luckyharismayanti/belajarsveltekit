<script>
	import KomikCard from '$lib/components/KomikCard.svelte';

	let keyword = '';
	let loading = false;
	/**
	 * @type {{img: string, title: string}[]}
	 */
	let items = [];
	const getData = async () => {
        loading = true;
		const resp = await fetch('https://bacabin.vercel.app/services/komikindo?q+keyword');
		const json = await resp.json();
        loading = false;
		items = json;
	};
	getData();
</script>

<form action="" on:submit|preventDefault={getData} class="flex justify-center items-center mb-4">
	<input
		type="text"
		class="bg-gray-200 rounded px-4 py-2"
		placeholder="Cari"
		bind:value={keyword}
	/>
</form>

<div class="grid grid-cols-6 px-20 gap-4 gap-y-8 gap-x-8">
    {#if loading}
    Lagi loading
    {:else}
	{#each items as item}
		<KomikCard image={item.img} title={item.title} />
	{/each}
    {/if}
</div>
