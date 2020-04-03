<section class="home-section">
    <h1>Home</h1>
    {#each posts as post}
        <article class="post">
            <h3 class="post__title">{ post.title }</h3>
            <p class="post__content">{ post.body }</p>
        </article>
    {/each}
</section>

<script>
    import { onMount } from "svelte";

    let posts = [];
    const API_URL = `https://jsonplaceholder.typicode.com/posts/`;

    async function getPosts() {
        const response = await fetch(API_URL);
        const data = await response.json();
        posts = data.slice(0, 10);
    }

    onMount(() => getPosts());
</script>

<style>
    .home-section {
        margin: 2.5rem auto;
        padding: 0 1rem;
        max-width: 70rem;
    }

    .post {
        width: 100%;
        margin: 2rem 0;
        padding: 2rem;
        border-radius: 4px;
        box-shadow: 0 2px 6px rgba(0,0,0,.2);
    }

</style>