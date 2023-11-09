<script>
	import User from './User.svelte';
 
	let users = [];

  async function fetchUserInfo() {
    try {
      const response = await fetch("https://randomuser.me/api");
      const mainObject = await response.json();
      return mainObject.results[0];
    } catch (error) {
      console.log("error", error);
    }
  }

	async function fetchAll(number) {
		users = [];
		for(let i = 0; i < number; i++) {
			const user = await fetchUserInfo();
			users = [...users, user];
		}
	}

</script>

<main>
  <button on:click={() => fetchAll(10)}>Fetch!</button>
  {#if users.length === 0}
    <p>No data</p>
  {:else}
		<div class="users-block">
			{#each users as user}
				<User user={user}/>
			{/each}
		</div>
  {/if}
</main>

<style>

	button {
		width: 200px;
		height: 50px;
		border-radius: 3px;
		background-color: dodgerblue;
	}

	.users-block {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		flex-wrap: wrap;
	}

  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
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
