<script>
	
	export let name;
	import { onMount } from 'svelte';
	let movies=[];
	let pagination={};
	


	async function getMovies() {


		fetch("http://localhost:3000/movies")
		.then((res) => res.json())
		.then((res) => {
			movies = res.data;
			pagination=res.pagination;
		});
	}

	onMount(() => {
		getMovies();
	});

</script>

<main>
	<h1 >{name}</h1>
	<div ></div>
	<div class=" mt-1 mb-2 w-100"></div>
	<div class="container  my-3">
		<table >
			<thead >
			  <tr>
				<th scope="col">Title</th>
				<th scope="col">Genres</th>
				<th scope="col">Year</th>
			  </tr>
			</thead>
			<tbody>
				{#each movies as movie }
					<tr>
						<td>{movie.title}</td>
						<td>
							{#each movie.genres as genre}
								{genre} , 
							{/each}
						</td>
						<td>{movie.year}</td>
					</tr>
				{/each}
			</tbody>
		</table>

	</div>	

</main>

