<script>
	let menu = 1;
	let email = "";
	getStandardUser();
	import Movie from "./Movie.svelte";
	import Artista from "./Artist.svelte";
	import Nav from "./Nav.svelte";
	import User from "./User.svelte";
	import UserList from "./UserList.svelte";
	import Favoritos from "./Favoritos.svelte";

	async function getStandardUser(id) {
		let res;
		if (id == null)
			res = await fetch(`http://localhost:8000/user/getUserById?id=1`);
		else
			res = await fetch(`http://localhost:8000/user/getUserById?id=${id}`);
		
		const text = await res.json();
		email = text.email;
		
	}
</script>

<Nav bind:menu/>

<div class="card">
	{#if menu === 1}
		<Movie bind:email/>
	{:else if menu === 2}
		<Favoritos bind:email/>
	{:else if menu === 3}
		<Artista/>
	{:else if menu === 4}
		<User bind:email/>
	{:else if menu === 5}
		<UserList bind:email/>
	{:else}
		OPTION 5
	{/if}
</div>