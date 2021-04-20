<script>
	import Container from 'sveltestrap/src/Container.svelte';
	import Navbar from "../components/Navbar.svelte";
	import Footer from '../components/Footer.svelte';
	import Sidebar from '../components/Sidebar.svelte';

	let theme = "dark";
	let color = "dark";
	let title = "Admin Svelte";

	export let segment;
</script>

<svelte:head>
	<title>{title}</title>
</svelte:head>

{#if segment !== "pages"}
	<div class="sb-nav-fixed">
		<Navbar {segment} {color} {title} />
		<div id="layoutSidenav">
			<Sidebar {segment} {theme} />
			<div id="layoutSidenav_content">
				<main>
					<Container fluid={true}>
						<slot />
					</Container>
				</main>
				<Footer />
			</div>
		</div>
	</div>
{:else}
	<body>
		<slot />
	</body>
{/if}
