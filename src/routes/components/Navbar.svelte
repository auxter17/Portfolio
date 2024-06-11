<!-- NavBar.svelte -->
<script>
	// Define navigation links
	let navLinks = [
		{ name: 'Home', url: '/' },
		{ name: 'About', url: '/about' },
		{ name: 'Skills', url: '/services' },
		{ name: 'Education', url: '/education' },
		{ name: 'Contact', url: '/contact' }
	];

	// Function to handle navigation
	function navigate(url) {
		window.location.href = url;
	}
</script>

<nav>
	<ul>
		{#each navLinks as link}
			<li class="my-auto">
				<a class="text-lg" href={link.url} on:click|preventDefault={() => navigate(link.url)}>
					{link.name}
				</a>
			</li>
		{/each}
	</ul>
</nav>

<style>
	/* Add your CSS styles for the navigation bar */
	nav {
		background-color: #d3d3d3;
		color: #fff;
		height: 80px;
		display: flex;
		justify-content: flex-end;
		border-bottom: 2px solid black;
	}

	ul {
		list-style-type: none;
		padding: 0;
		margin: 0;
		display: flex;
		gap: 50px;
		padding-right: 20px;
	}

	li {
		padding: 10px 30px;
		cursor: pointer;
	}

	li:hover {
		background-color: #555;
	}

	a {
		font-weight: bold;
		color: black;
		text-decoration: none;
	}
</style>
