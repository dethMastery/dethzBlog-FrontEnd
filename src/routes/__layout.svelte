<script lang="ts">
	import '../app.css';
</script>

<main>
	<slot />
</main>

<footer>
	&copy; 2022 <a href="https://suphakit.net">Suphakit P.</a> All Right Reserved.
</footer>

<style>
	footer {
		width: 100%;
		padding-top: 1.5rem;
		padding-bottom: 1.5rem;

		background-color: whitesmoke;

		text-align: center;
	}
</style>
