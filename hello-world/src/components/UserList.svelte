<script>
    import {createEventDispatcher, onMount} from "svelte";

    export let pageName = '';
    let users = [];

    const dispatch = createEventDispatcher();

    onMount(async () => {
        const res = await fetch('https://jsonplaceholder.typicode.com/users');
        users = await res.json();
    });
</script>
<main>
    <div class="name-list">
        <h3>{pageName}</h3>
        <h5> User List</h5>
        {#each users as user (user.id)}
            <div><span>Name: {user.name}</span><br /><span>Email: {user.email}</span></div><br />
        {/each}

        <button type="button" on:click={() => dispatch("close", 'data')}>Send Custom Event</button>
    </div>
</main>