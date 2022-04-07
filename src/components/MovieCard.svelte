<script>
    export let movie;
</script>



<div class="movie-card">
        <a href={"/movie/" + movie.id} >
        <img src={'https://image.tmdb.org/t/p/w500' + movie.poster_path} alt="{movie.title}" class="movie-image">
        </a>
        <div class="description">
    <h2>{movie.title}</h2>
<p class="movie-release">{movie.release_date}</p>

</div>
</div>



<style>

    img {
        width: 100%;
        height: 40vh;
        object-fit: cover;
        border-radius: 1rem;
        margin-bottom: 1rem;
    }

    .description {
        height: 5vh;
    }

    p {
        font-size: 0.7rem;
    }

    .movie-card {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        padding: 1rem;
    }
</style>