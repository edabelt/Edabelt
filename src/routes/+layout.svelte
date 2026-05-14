<script>
	import 'bulma/css/bulma.min.css';
	import '../app.css';
	import { page } from '$app/state';

	let { children } = $props();

	let isMenuOpen = $state(false);

	const isSpanish = () => page.url.pathname.startsWith('/es');

	function toggleMenu() {
		isMenuOpen = !isMenuOpen;
	}

	function closeMenu() {
		isMenuOpen = false;
	}
</script>

<nav class="navbar is-light" aria-label="main navigation">
	<div class="container is-fluid">
		<div class="navbar-brand">
			<a
				class="navbar-item has-text-weight-semibold"
				href={isSpanish() ? '/es' : '/'}
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

		<div
			class="navbar-menu"
			class:is-active={isMenuOpen}
		>
			<div class="navbar-end">
				{#if isSpanish()}
					<a class="navbar-item" href="/es/about" onclick={closeMenu}>
						Sobre mí
					</a>

					<a class="navbar-item" href="/es/cv" onclick={closeMenu}>
						CV
					</a>

					<a class="navbar-item" href="/es/writing" onclick={closeMenu}>
						Escritura
					</a>

					<a class="navbar-item" href="/es/projects" onclick={closeMenu}>
						Proyectos
					</a>

					<a class="navbar-item" href="/es/contact" onclick={closeMenu}>
						Contacto
					</a>
				{:else}
					<a class="navbar-item" href="/about" onclick={closeMenu}>
						About
					</a>

					<a class="navbar-item" href="/cv" onclick={closeMenu}>
						CV
					</a>

					<a class="navbar-item" href="/writing" onclick={closeMenu}>
						Writing
					</a>

					<a class="navbar-item" href="/projects" onclick={closeMenu}>
						Projects
					</a>

					<a class="navbar-item" href="/contact" onclick={closeMenu}>
						Contact
					</a>
				{/if}

				<div class="navbar-item language-switcher">
					<a href="/" onclick={closeMenu}>
						🇬🇧 EN
					</a>

					<span class="mx-2">|</span>

					<a href="/es" onclick={closeMenu}>
						🇪🇸 ES
					</a>
				</div>
			</div>
		</div>
	</div>
</nav>

{@render children()}

<footer class="site-footer">
	<div class="content has-text-centered">
		<p class="mb-1">
			© 2026 Ever David Beltrán Pinto
		</p>

		{#if isSpanish()}
			<p class="mb-1">
				Computación, investigación y escritura en cultura digital.
			</p>
		{:else}
			<p class="mb-1">
				Computing, research, and writing across digital culture.
			</p>
		{/if}

		<p>
			<a href="mailto:edbeltranpi.chs@gmail.com">
				edbeltranpi.chs@gmail.com
			</a>

			·

			<a
				href="https://www.linkedin.com/in/davidbeltranpinto/"
				target="_blank"
				rel="noopener noreferrer"
			>
				LinkedIn
			</a>

			·

			<a
				href="https://github.com/edabelt"
				target="_blank"
				rel="noopener noreferrer"
			>
				GitHub
			</a>
		</p>
	</div>
</footer>