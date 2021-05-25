<script lang="ts">
import Clock from "./Clock.svelte";

</script>

<main>
	<div>
		<Clock/>
	</div>
</main>

<style>
	main {
		display: grid;
    height: 100%;
    align-content: center;
		padding-left: 3rem;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>