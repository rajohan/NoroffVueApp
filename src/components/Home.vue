<template>
    <span class="loading" v-if="isLoading">Loading...</span>
    <div v-else class="recipes">
        <div v-for="(recipe, key) in recipes" v-bind:key="`recipe-${key}`">
            <RecipeCard v-bind:image="recipe.thumbnail"
                        v-bind:title="recipe.title"
                        v-bind:link="recipe.href"
                        v-bind:ingredients="recipe.ingredients"
            />
        </div>
    </div>
</template>

<script>
    import RecipeCard from "./RecipeCard";

    export default {
        name: "Recipes",
        components: {
            RecipeCard
        },
        data() {
          return {
              isLoading: true,
              recipes: []
          }
        },
        created: function () {
            const corsUrl = "https://cors-anywhere.herokuapp.com/";
            const url = "http://www.recipepuppy.com/api/";

            fetch(corsUrl + url).then(response => {
                return response.json();
            }).then(result => {
                this.recipes = result.results;

                // Create array from ingredients string and remove duplicate ingredients
                this.recipes.map(recipe => {
                    recipe.ingredients = recipe.ingredients.split(",");
                    recipe.ingredients = [...new Set(recipe.ingredients)];
                });

                this.isLoading = false;
            });
        }
    }
</script>

<style scoped>
    .recipes {
        display: grid;
        width: 100%;
        max-width: 1250px;
        margin-top: 15px;
        grid-gap: 15px;
        grid-template-columns: repeat(auto-fill, minmax(300px, 300px));
        justify-content: center;
    }

    .loading {
        margin-top: 20px;
    }
</style>
