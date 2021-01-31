<script>
  export let movies;
</script>

<div class="movie__list">
    {#each movies as movie (movie.title)}
        <div class="movie__item">
            <h3>{movie.title}</h3>
            <p>Your rating: {movie.rating}</p>
        </div>
    {/each}
    
</div>

<style>
  .movie__list{
    display: flex;
    padding: 0;
    margin: 0;
    flex-direction: column;
    align-items: flex-start;
    box-sizing: border-box;
  }
  .movie__item{
      width: 100%;
      display: flex;
      flex-direction: column;
      text-align: start;
      border-bottom: 2px solid rgba(0,0,0,0.6);
  }
</style>