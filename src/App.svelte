<script>
	import MovieList from './components/MovieList.svelte';
	import MovieInput from "./components/MovieInput.svelte";
	import Search from './components/Search.svelte';

	let movies=localStorage.getItem('movies')?
			  JSON.parse(localStorage.getItem('movies')):[];
			  
	const submitMovie = movie =>{
		const updatedMovies= [...movies, movie ];
		localStorage.setItem('movies', JSON.stringify(updatedMovies));
		movies = updatedMovies;
	}
	const clearSearch =()=>{
		movies=localStorage.getItem('movies')?
			  JSON.parse(localStorage.getItem('movies')):[];
	}
	const search = searchTerm =>{
		let tempMovies =localStorage.getItem('movies')?
			  JSON.parse(localStorage.getItem('movies')):[];
		movies =tempMovies.filter(m=>m.title.toLowerCase().includes(searchTerm.toLowerCase()));
	}
</script>

<main>
	<h1>MOVIE Journal</h1>
	<Search on:search={event=>search(event.detail.searchTerm)} on:clearSearch={clearSearch}/>
	<MovieInput on:submitMovie={e=>submitMovie(e.detail.movie)}/>
	<MovieList movies={movies} />
</main>

<style>
	main{
		width: 500px;
		max-width: 100%;
		padding: 1rem;
		margin: auto;
		text-align: center;
	}
	h1{
		color:#ff3e00;
		font-weight: 100;
		text-transform: uppercase;
		font-size: 4rem;
	}
</style>