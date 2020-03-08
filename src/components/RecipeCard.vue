<template>
    <div class="card">
        <h2>{{title}}</h2>
        <img crossorigin="anonymous" :src="`https://cors-anywhere.herokuapp.com/${image}`" alt="recipe image">
        <h3>Ingredients</h3>
        <ol>
            <li v-for="(ingredient, key) in ingredients" v-bind:key="key">
                {{ingredient}}
            </li>
        </ol>
        <a :href="link" target="_blank">View Recipe</a>
    </div>
</template>

<script>
    export default {
        name: "RecipeCard",
        props: ["image", "title", "link", "ingredients"]
    }
</script>

<style scoped>
    .card {
        border: 1px solid #ffffff;
        height: 100%;
        padding: 10px;
        display: flex;
        flex-direction: column;
        align-items: center;
        background-color: rgba(249, 249, 249, 1);
        color: black;
        border-radius: 2px;
        box-shadow: 0 0 10px 0 rgba(255,255,255,0.5);
    }

    .card h2 {
        font-size: 18px;
    }

    .card h3 {
        font-size: 15px;
        margin-bottom: 0;
        text-decoration: underline;
    }

    .card img {
        min-width: 80px;
        min-height: 80px;
        border-radius: 3px;
        border: 1px solid #000;
    }

    .card ol {
        display: grid;
        grid-template-columns: auto auto;
        padding: 0;
        list-style-type: none;
        white-space: nowrap;
        width: 100%;
        height: 100%;
        justify-content: space-evenly;
        align-content: flex-start;
    }

    .card li {
        text-transform: capitalize;
    }

    .card a {
        text-decoration: none;
        color: #fff;
        padding: 10px;
        width: 200px;
        text-align: center;
        background-color: #ff5b56;
        border-radius: 3px;
        margin-bottom: 5px;
    }

    .card a:hover {
        background-color: #ff332c;
    }
</style>