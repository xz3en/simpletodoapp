<script lang="ts">
    import { onMount } from "svelte";

    let todos: string[] = [];
    let todoText: string = "";

    onMount(() => {
        todos = JSON.parse(localStorage.getItem("todos.json") || "[]");
    });

    function addTodo(todo: any) {
        todos = [...todos,todoText];
        localStorage.setItem("todos.json",JSON.stringify(todos));
    }

    function clearTodo() {
        todos = [];
        localStorage.setItem("todos.json","[]");
    }
</script>

<style>
    
</style>

<main class="bg-dark">
    <html lang="en" data-bs-theme="dark">
        <head>
            <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-4bw+/aepP/YC94hEpVNVgiZdgIC5+VKNBQNGCHeKRQN+PtmoHDEXuppvnDJzQIu9" crossorigin="anonymous">
        </head>
        <body>
            <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-HwwvtgBNo3bZJJLYd8oVXjrBZt8cqVSpeBNS5n7C8IVInixGAoxmnlMuBnhbgrkm" crossorigin="anonymous"></script>

            <div>
                <form class="m-5" on:submit|preventDefault={addTodo}>
                    <input bind:value={todoText}>
                    <input type="submit" value="Add todo">
                </form>
            
                <ul class="m-5">
                    {#each todos as todo}
                        <li>{todo}</li>
                    {/each}
                </ul>
            </div>
        </body>
    </html>
</main>