<script context="module">
    
    const urlString = `https://api.themoviedb.org/3/movie/popular?api_key=00f18f62f1339acd38f45ceabf0531b5`


    export async function load({fetch}) {
        const res = await fetch (
            urlString+`&page=1`
        );

    let arrayOfMovies = []

    function addMoviesToArray(res) {
        // console.log(data)
        // arrayOfMovies.push(res.json())
    }
        const res1 = Promise.all([
            fetch (urlString+`&page=1`).then(res => res.json()),
            fetch (urlString+`&page=2`).then(res => res.json()),
            fetch (urlString+`&page=3`).then(res => res.json()),
            fetch (urlString+`&page=4`).then(res => res.json()),
            fetch (urlString+`&page=5`).then(res => res.json()),
            fetch (urlString+`&page=6`).then(res => res.json()),
            fetch (urlString+`&page=7`).then(res => res.json()),
            fetch (urlString+`&page=8`).then(res => res.json()),
            fetch (urlString+`&page=9`).then(res => res.json()),
            fetch (urlString+`&page=10`).then(res => res.json()),
            fetch (urlString+`&page=11`).then(res => res.json()),
            fetch (urlString+`&page=12`).then(res => res.json()),
            fetch (urlString+`&page=13`).then(res => res.json()),
            fetch (urlString+`&page=14`).then(res => res.json()),
            fetch (urlString+`&page=15`).then(res => res.json()),
        ]).then((value) => {
            // arrayOfMovies = res.clone().json();
            for(let i = 0; i<value.length; i++) {
                // console.log(value[i].results)
                arrayOfMovies = arrayOfMovies.concat(value[i].results)

            }
            return arrayOfMovies;
        })

        let data = await res1;

        // console.log(arrayOfMovies)
        // console.log(data)
        if(res.ok) {
            return {
                props: {
                    popular: data
                }
            }
        }
    }

   // import { onMount } from 'svelte'
</script>


 
<script>
import SearchMovies from "../components/SearchMovies.svelte";
import PopularMovies from "../components/PopularMovies.svelte";
import global from '../global.css'



export let popular;
console.log(popular)

let searchTerm = '';

let filteredMovies = popular;

const searchMovies = () => {
    return filteredMovies = popular.filter(movie => {
        return movie.title.toLowerCase().includes(searchTerm.toLowerCase());
    })
}

$: console.log(filteredMovies)


</script>

    <SearchMovies 
    bind:searchTerm
    on:input={searchMovies}
    />
    <PopularMovies 
        popular={filteredMovies}
    />

<style>

</style>