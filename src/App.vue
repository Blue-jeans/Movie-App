<template>
<div class="App">
    <Header :title="'Movies'" />
    <Search :search="state.search" @search="handleSearch" />

    <div class="movies">
        <Movie v-for="movie in state.movies" :movie="movie" :key="movie.imdbID" />
    </div>
</div>
</template>

<script>
import Header from './components/Header.vue';
import Search from './components/Search';
import Movie from './components/Movie.vue';
import {
    useMovieApi
} from './hooks/movie-api';

export default {
    name: 'app',
    components: {
        Header,
        Search,
        Movie
    },
    setup() {
        const state = useMovieApi();

        return {
            state,
            handleSearch(searchTerm) {
                state.loading = true;
                state.search = searchTerm;
            }
        };
    }
}
</script>

<style>
body {
    background-color: #D5B9B2
}

.app {
    text-align: center;
}

.header {
    background-color: #282c34;
    height: 70px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: calc(10px + 2vmin);
    color: white;
    padding: 20px;
    cursor: pointer;
}

.spinner {
    height: 80px;
    margin: auto;
}

.intro {
    font-size: large;
}

/* new css for movie component */

* {
    margin: 0;
    padding: 0;
    font-family: 'Fira Sans', sans-serif;
    box-sizing: border-box;
}

.movies {
    display: grid;
    /* try to fit as many as you can, shouldn't be smaller than 320, 
    once it gets to 320 go to another row. max 1fr */
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    padding-bottom: 50px;
    padding-top: 50px;
}

.header h2 {
    margin: 0;
}

.add-movies {
    text-align: center;
}

.add-movies button {
    font-size: 16px;
    padding: 8px;
    margin: 0 10px 30px 10px;
}

.movie {
    padding: 5px 25px 10px 25px;
    max-width: 25%;
}

.errorMessage {
    margin: auto;
    font-weight: bold;
    color: rgb(161, 15, 15);
}

.search {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    margin-top: 10px;
}

input[type="submit"] {
    padding: 5px;
    background-color: transparent;
    color: black;
    border: 1px solid black;
    width: 80px;
    margin-left: 5px;
    cursor: pointer;
}

input[type="submit"]:hover {
    background-color: #282c34;
    color: antiquewhite;
}

.search>input[type="text"] {
    width: 40%;
    min-width: 170px;
}

@media screen and (min-width: 694px) and (max-width: 915px) {
    .movie {
        max-width: 33%;
    }
}

@media screen and (min-width: 652px) and (max-width: 693px) {
    .movie {
        max-width: 50%;
    }
}

@media screen and (max-width: 651px) {
    .movie {
        max-width: 100%;
        margin: auto;
    }
}
</style>
