<script>
	import { counter } from "$lib/stores/counter";
	import { createEventDispatcher } from "svelte";


	$: if ($counter < 0) $counter = 0;

	$: double = $counter * 2;
	$: trippled = $counter * 3;

    
    const dispatch = createEventDispatcher()

</script>

<div class="flex items-center gap-4">
	<button
		type="button"
		class="px-4 py-2 rounded bg-blue-600 text-white"
		on:click={() => {
			$counter--;
            dispatch('decrement')
		}}
	>
		-
	</button>
	<p>{$counter}</p>
	<button
		type="button"
		class="px-4 py-2 rounded bg-blue-600 text-white"
		on:click={() => {
			$counter++;
            dispatch('increment', $counter)
		}}
	>
		+
	</button>
</div>

<div class="mt-4">
	<p>{$counter}x2={double}</p>
	<p>{$counter}x3={trippled}</p>
</div>
