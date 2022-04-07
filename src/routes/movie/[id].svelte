<script context="module">
    
    export async function load({fetch, params}) {
        const movieId = params.id
        const res = await fetch (
            `https://api.themoviedb.org/3/movie/` + movieId + `?api_key=00f18f62f1339acd38f45ceabf0531b5`

            // `https://api.themoviedb.org/3/genre/movie?api_key=00f18f62f1339acd38f45ceabf0531b5`
        );

        const data = await res.json();
        console.log(data)
        if(res.ok) {
            return {
                props: {
                    movie: data
                }
            }
        }
    }

   // import { onMount } from 'svelte'
</script>

<script>
    export let movie;
</script>


<div class="movie-details">
    <div class="img-container">
    <img src={"https://image.tmdb.org/t/p/original" + movie.backdrop_path} alt="{movie.title}" class="movie-detail">
    </div>

    <div class="text-container">
        <h1>{movie.title}</h1>
    <p class="overview">{movie.overview}</p>
    <p><span>Release Date:</span> {movie.release_date}</p>
    <p><span>Budget:</span> {movie.budget}</p>
    <p><span>Rating:</span> {movie.vote_average}</p>
    <p><span>Runtime</span> {movie.runtime}</p>

    </div>
</div>


<style>

    h1 {
        padding: 1rem 0rem 2rem;
    }

    p {
        padding: 1rem 0rem;
    }

    .img-container {
        width: 100%;
    }

    img {
        width: 100%;
        border-radius: 1rem;
    }

    .movie-details {
        margin: 2rem 20%;
    }
    span {
        font-weight: bold;
    }
</style>