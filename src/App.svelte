<script>
	import Navbar from './Navbar.svelte'
	import Player from './Player.svelte'
	import AddPlayer from './AddPlayer.svelte'

	let players = [
		{
			name: 'Squirly Dan',
			points: 35
		},
		{
			name: 'Chubbs Peterson',
			points: 90
		},
		{
			name: 'Barron Trump',
			points: 3
		},
	]

	const addPlayer = (e) => {
		const newPlayer = e.detail
		players = [...players, newPlayer]
	}

	const deletePlayer = (e) => {
		players = players.filter(p => p.name != e.detail)
	}

</script>

<main>
<Navbar></Navbar>
<div class="container">
	<AddPlayer on:addplayer={addPlayer} ></AddPlayer>
	{#if players.length === 0}
		<p>No Players</p>
	{:else}
		{#each players as player}
			<Player name={player.name} points={player.points} on:deleteplayer={deletePlayer}></Player>
		{/each}
	{/if}

</div>
	
</main>

<style>


</style>