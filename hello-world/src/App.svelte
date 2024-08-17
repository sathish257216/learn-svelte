<script>
	import UserList from "./components/UserList.svelte";
	
	export let name;
	const msg = "<b>Welcome to the Svelte</b>";
	const isAttr = 'msg-text';
	const isDisabled = false;
	let num = 1;

	let signupForm = {
		name: "signup",
		email: "",
		mobile: ""
	}

	$: nameEmail = signupForm.name + " " + signupForm.email;
	const handleClick = () => {
		console.log("handleClick ");
	}

	const onSubmitForm = () => {
		console.log('onSubmitForm', signupForm);
	}
</script>

<main>
	<h1>Hello {name}!</h1>
	<span>{ @html msg}</span>
	<p id={isAttr}>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<button disabled={isDisabled} class:disable-btn={isDisabled} on:click={handleClick}>Next</button>

	<br/>
	<div class="parent-container">
		<div>
			{#if num == 0}
				<h3> Number is Zero</h3>
			{:else if num < 0}
				<h3> Number is negative</h3>
			{:else if num > 100}
				<h3> Number is greater than 100</h3>
			{:else}
				<h3> Number is less than 100</h3>
			{/if}
		</div>
		<br/>
		<UserList pageName={'Home'} on:close={($event)=> console.log("custom Event", $event.detail)}/>
		<br/>
		<div class="signup-form">
			<h2>Signup</h2>
			<pre>{JSON.stringify(signupForm)	}</pre>
			<form on:submit={onSubmitForm}>
			<div class="form-field">
				<label for="name">Name</label>
				<input type="text" id="name" bind:value={signupForm.name} />
			</div>
			<div class="form-field">
				<label for="email">Email</label>
				<input type="text" id="email" bind:value={signupForm.email} />
			</div>
			<div class="form-field">
				<label for="mobile">Mobile</label>
				<input type="text" id="mobile" bind:value={signupForm.mobile} />
			</div>

			<button type="submit" class="submit-btn" id="submit-form">Submit</button>
			</form>
		</div>
		</div>
			<br />
		<div>
			<h6>Reactive Decleration</h6>
			<span>{nameEmail}</span>
		</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	.parent-container {
		padding: 20px;
	}
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>