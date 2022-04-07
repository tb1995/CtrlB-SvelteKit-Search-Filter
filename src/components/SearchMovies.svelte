<script>
    export let searchTerm = '';
    let active = false;

    function cancelInactive() {
        if (searchTerm) {
            active = true
        } else {
            active = false
        }
    }
</script>

<form class="search">

    {#if !active}
        <label for="search_movie" ></label>      
    {/if}
    <input 
     onfocus={() => (active=true)}
     onblur={cancelInactive}
     bind:value= {searchTerm}
     name="search_movie"
     type="text"
     class={active ? 'selected' : ''}
     placeholder="Search Movies"
     on:input
     />

    <!-- {#if searchTerm}
        <button>Search</button>
    {/if} -->
</form>


<style>

    .search {
        position: relative;
        width: 30%;
        margin: 1rem;
    }

    button {
        font-size: 0.7rem;
        padding: 0rem 1rem;
        background: rgb(96, 110, 201);
        color: white;
        font-weight: bold;
        border: none;
        position: absolute;
        bottom: 50%;
        right: 0;
        transform: translate(0, 50%);
        height: 100%;

    }

    input {
        width: 100%;
        border: none;
        font-size: 1rem;
        font-family: 'Poppins', sans-serif;
        outline: none;
        color: white;
        padding: 0.5rem 0.1rem;
        transition: background 0.75s ease-out;
        font-weight: bold;
        background: rgb(63, 63, 63);
        border-radius: 10px;
        padding: 1rem
    }

    label {
        position: absolute;
        font-size: 0.8rem;
        top: 20%;
        left: 0;
        transform: translate(0, 50%);
        pointer-events: none;
        color: white;
        padding: 0rem 1rem;
    }

    input.selected {
        background: rgb(50, 50, 50);
    }
</style>