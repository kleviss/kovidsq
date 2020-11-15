<script>
	import { onMount } from "svelte";

	const api = "https://coronavirus-19-api.herokuapp.com/countries/Albania";
	let data = {};

	onMount(async () => {
		let rezultati = await fetch(api);
		data = await rezultati.json();
	});
</script>

<style>
</style>

<main>
	<div class="text-center">
		<img
			src="https://www.flaticon.com/svg/static/icons/svg/299/299849.svg"
			alt="Flamuri Shqiptar"
			class="mt-4"
			style="width: 75px" />

		<h1 class="my-4">
			Covid Stats for
			<!-- svelte-ignore empty-block -->
			{#if data.country == undefined}{:else}{data.country}{/if}
		</h1>

		<a href="tel:129" class="btn btn-outline-danger">Telefono Urgjencen</a>
	</div>

	<div class="container">
		<h2 class="my-4">Statistika</h2>
		<p>Shifrat e pergjithshme te Koronavirusit ne Shqiperi deri tani.</p>

		<div class="row">
			<div class="col">
				<div class="card shadow-sm">
					<div class="card-body text-center">
						<p class="mb-0 lead">Raste</p>
						{#if data.cases == undefined}
							<div class="spinner-border text-dark" role="status">
								<span class="sr-only">Loading...</span>
							</div>
						{:else}
							<h1 class="mb-0">{data.cases}</h1>
						{/if}
					</div>
				</div>
			</div>

			<div class="col">
				<div class="card shadow-sm">
					<div class="card-body text-center">
						<p class="mb-0 lead">Te Sheruar</p>
						{#if data.recovered == undefined}
							<div
								class="spinner-border text-success"
								role="status">
								<span class="sr-only">Loading...</span>
							</div>
						{:else}
							<h1 class="mb-0 text-success">{data.recovered}</h1>
						{/if}
					</div>
				</div>
			</div>

			<div class="col">
				<div class="card shadow-sm">
					<div class="card-body text-center">
						<p class="mb-0 lead">Vdekje</p>
						{#if data.recovered == undefined}
							<div
								class="spinner-border text-danger"
								role="status">
								<span class="sr-only">Loading...</span>
							</div>
						{:else if data.deaths == 0}
							<h1 class="mb-0 text-success">{data.todayCases}</h1>
						{:else}
							<h1 class="mb-0 text-danger">{data.deaths}</h1>
						{/if}
					</div>
				</div>
			</div>
		</div>

		<h2 class="my-4">Sot</h2>
		<p>Shifrat e sotme te Koronavirusit ne Shqiperi.</p>

		<div class="row">
			<div class="col">
				<div class="card shadow-sm">
					<div class="card-body text-center">
						<p class="mb-0 lead">Raste</p>
						{#if data.todayCases == undefined}
							<div
								class="spinner-border text-success"
								role="status">
								<span class="sr-only">Loading...</span>
							</div>
						{:else if data.todayCases == 0}
							<h1 class="mb-0 text-success">{data.todayCases}</h1>
						{:else}
							<h1 class="mb-0 text-danger">{data.todayCases}</h1>
						{/if}
					</div>
				</div>
			</div>

			<div class="col">
				<div class="card shadow-sm">
					<div class="card-body text-center">
						<p class="mb-0 lead">Vdekje</p>
						{#if data.todayDeaths == undefined}
							<div
								class="spinner-border text-success"
								role="status">
								<span class="sr-only">Loading...</span>
							</div>
						{:else if data.todayDeaths == 0}
							<h1 class="mb-0 text-success">{data.todayCases}</h1>
						{:else}
							<h1 class="mb-0 text-danger">{data.todayDeaths}</h1>
						{/if}
					</div>
				</div>
			</div>
		</div>

		<h2 class="my-4">Te tjera</h2>
		<p>Shifrat e te tjera te pergjithshme te Koronavirusit ne Shqiperi.</p>

		<div class="row">
			<div class="col">
				<div class="card shadow-sm">
					<div class="card-body text-center">
						<p class="mb-0 lead">Raste aktive</p>
						{#if data.active == undefined}
							<div class="spinner-border text-dark" role="status">
								<span class="sr-only">Loading...</span>
							</div>
						{:else if data.active == 0}
							<h1 class="mb-0">{data.active}</h1>
						{:else}
							<h1 class="mb-0">{data.active}</h1>
						{/if}
					</div>
				</div>
			</div>

			<div class="col">
				<div class="card shadow-sm">
					<div class="card-body text-center">
						<p class="mb-0 lead text-success">Teste Totale</p>
						{#if data.totalTests == undefined}
							<div class="spinner-border text-dark" role="status">
								<span class="sr-only">Loading...</span>
							</div>
						{:else if data.totalTests == 0}
							<h1 class="mb-0">{data.totalTests}</h1>
						{:else}
							<h1 class="mb-0">{data.totalTests}</h1>
						{/if}
					</div>
				</div>
			</div>

			<div class="col">
				<div class="card shadow-sm">
					<div class="card-body text-center">
						<p class="mb-0 lead text-danger">Raste Kritike</p>
						{#if data.critical == undefined}
							<div
								class="spinner-border text-danger"
								role="status">
								<span class="sr-only">Loading...</span>
							</div>
						{:else if data.critical == 0}
							<h1 class="mb-0 text-danger">{data.critical}</h1>
						{:else}
							<h1 class="mb-0 text-danger">{data.critical}</h1>
						{/if}
					</div>
				</div>
			</div>
		</div>
	</div>

	<div class="text-center my-4 text-muted">
		<p>
			Zhvilluar nga
			<a
				href="https://www.linkedin.com/in/klevis-xhyra/"
				target="_blank">klev_s</a>
		</p>

		<p>
			Tutoriali nga
			<a
				href="https://sputnik.al/"
				target="_blank">sputnik.al</a>
		</p>
	</div>
</main>
