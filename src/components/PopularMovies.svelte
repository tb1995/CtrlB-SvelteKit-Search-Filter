<script>
import MovieCard from "./MovieCard.svelte";

    export let popular;
</script>

<h1> Popular Movies </h1>

<div class="popular-movies">
    {#each popular as movie}
        <MovieCard 
            {movie}
        />
    {/each}
</div>


<style>

h1 {
    padding: 0 1rem;
}

.popular-movies {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-column-gap: 1rem;
    grid-row-gap: 2rem;
    margin: 0 auto;
}

</style>