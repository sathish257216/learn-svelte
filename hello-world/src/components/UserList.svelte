<script>
    import {createEventDispatcher} from "svelte";

    export let pageName = '';
    let users = ["Smith", "Jhon", "Tom"];

    const dispatch = createEventDispatcher();
</script>
<main>
    <div class="name-list">
        <h3>{pageName}</h3>
        <h5> User List</h5>
        {#each users as user, index (user)}
            <div><span>{index+1}. {user}</span></div>
        {/each}

        <button type="button" on:click={() => dispatch("close", 'data')}>Send Custom Event</button>
    </div>
</main>