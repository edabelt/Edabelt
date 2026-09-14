<script>
	import 'bulma/css/bulma.min.css';
	import '../app.css';
	import { browser } from '$app/environment';
	import { afterNavigate } from '$app/navigation';
	import { onMount } from 'svelte';

	let { children, data } = $props();

	let isMenuOpen = $state(false);
	let routePath = $state('');

	const currentPath = $derived(normalizePath(routePath || data.pathname));
	const isSpanish = $derived(currentPath.startsWith('/es'));
	const backHref = $derived.by(() => {
		if (currentPath.startsWith('/es/writing/')) return '/es/writing';
		if (currentPath.startsWith('/writing/')) return '/writing';

		return isSpanish ? '/es' : '/';
	});
	const backLabel = $derived.by(() => {
		if (currentPath.startsWith('/es/writing/')) return 'Volver a escritura';
		if (currentPath.startsWith('/writing/')) return 'Back to writing';

		return isSpanish ? 'Volver al inicio' : 'Back home';
	});

	function normalizePath(path) {
		return path.replace(/\/$/, '') || '/';
	}

	function closeMenu() {
		isMenuOpen = false;
	}

	function toggleMenu() {
		isMenuOpen = !isMenuOpen;
	}

	onMount(() => {
		routePath = normalizePath(window.location.pathname);
	});

	afterNavigate(({ to }) => {
		routePath = normalizePath(
			to?.url.pathname || (browser ? window.location.pathname : data.pathname)
		);
	});
</script>

<nav class="navbar is-light" aria-label="main navigation">
	<div class="container is-fluid">
		<div class="navbar-brand">
			<a
				class="navbar-item has-text-weight-semibold"
				href={isSpanish ? '/es' : '/'}
				onclick={closeMenu}
			>
				EB
			</a>

			<button
				type="button"
				class="navbar-burger"
				class:is-active={isMenuOpen}
				aria-label="menu"
				aria-expanded={isMenuOpen}
				onclick={toggleMenu}
			>
				<span aria-hidden="true"></span>
				<span aria-hidden="true"></span>
				<span aria-hidden="true"></span>
			</button>
		</div>

		<div class="navbar-menu" class:is-active={isMenuOpen}>
			<div class="navbar-end">
				<a class="navbar-item" href={isSpanish ? '/es' : '/'} onclick={closeMenu}>
					{isSpanish ? 'Inicio' : 'Home'}
				</a>

				<a class="navbar-item" href={isSpanish ? '/es/about' : '/about'} onclick={closeMenu}>
					{isSpanish ? 'Sobre mí' : 'About'}
				</a>

				<a
					class="navbar-item"
					href={isSpanish ? '/es/cv' : '/cv'}
					data-sveltekit-reload
					onclick={closeMenu}
				>
					CV
				</a>

				<a class="navbar-item" href={isSpanish ? '/es/writing' : '/writing'} onclick={closeMenu}>
					{isSpanish ? 'Escritura' : 'Writing'}
				</a>

				<a class="navbar-item" href={isSpanish ? '/es/projects' : '/projects'} onclick={closeMenu}>
					{isSpanish ? 'Proyectos' : 'Projects'}
				</a>

				<a class="navbar-item" href={isSpanish ? '/es/leisure' : '/leisure'} onclick={closeMenu}>
					{isSpanish ? 'Ocio' : 'Leisure'}
				</a>

				<a class="navbar-item" href={isSpanish ? '/es/contact' : '/contact'} onclick={closeMenu}>
					{isSpanish ? 'Contacto' : 'Contact'}
				</a>

				<div class="navbar-item language-switcher">
					<a href="/" onclick={closeMenu}> 🇬🇧 EN </a>

					<span class="mx-2">|</span>

					<a href="/es" onclick={closeMenu}> 🇪🇸 ES </a>
				</div>
			</div>
		</div>
	</div>
</nav>

<div
	class="page-back-shell"
	aria-label={isSpanish ? 'Navegación secundaria' : 'Secondary navigation'}
>
	<a class="page-back-link" href={backHref}>
		<span aria-hidden="true">←</span>
		{backLabel}
	</a>
</div>

{@render children()}

<footer class="site-footer">
	<div class="content has-text-centered">
		<p class="mb-1">© 2026 Ever David Beltrán Pinto</p>

		<p class="mb-1">
			{isSpanish
				? 'Computación, investigación y escritura en cultura digital.'
				: 'Computing, research, and writing across digital culture.'}
		</p>

		<p>
			<a href="mailto:edbeltranpi.chs@gmail.com"> edbeltranpi.chs@gmail.com </a>

			·

			<a
				href="https://www.linkedin.com/in/davidbeltranpinto/"
				target="_blank"
				rel="noopener noreferrer"
			>
				LinkedIn
			</a>

			·

			<a href="https://github.com/edabelt" target="_blank" rel="noopener noreferrer"> GitHub </a>
		</p>
	</div>
</footer>
