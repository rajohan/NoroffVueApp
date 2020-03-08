<template>
    <div id="app">
        <h1>Recipe Puppy</h1>
        <Recipe />
    </div>
</template>

<script>
    import Recipe from "./components/Home";
    export default {
        name: "App",
        components: {
            Recipe
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
    }

    body {
        background-color: #262626;
    }

    #app {
        color: #fff;
        max-width: 100vw;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-bottom: 40px;
    }
</style>
