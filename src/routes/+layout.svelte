<script>
	import 'bulma/css/bulma.min.css';
	import '../app.css';
	import { page } from '$app/state';

	let { children } = $props();

	const isSpanish = () => page.url.pathname.startsWith('/es');
</script>

<nav class="navbar px-5 py-4" role="navigation">
	<div class="navbar-brand">
		<a class="navbar-item has-text-weight-semibold" href={isSpanish() ? '/es' : '/'}>EB</a>
	</div>

	<div class="navbar-menu is-active">
		<div class="navbar-end">
			{#if isSpanish()}
				<a class="navbar-item" href="/es/about">Sobre mí</a>
				<a class="navbar-item" href="/es/cv">CV</a>
				<a class="navbar-item" href="/es/writing">Escritura</a>
				<a class="navbar-item" href="/es/projects">Proyectos</a>
				<a class="navbar-item" href="/es/contact">Contacto</a>
			{:else}
				<a class="navbar-item" href="/about">About</a>
				<a class="navbar-item" href="/cv">CV</a>
				<a class="navbar-item" href="/writing">Writing</a>
				<a class="navbar-item" href="/projects">Projects</a>
				<a class="navbar-item" href="/contact">Contact</a>
			{/if}

			<span class="navbar-item language-divider">|</span>

			<a class="navbar-item" href="/">🇬🇧 EN</a>
			<a class="navbar-item" href="/es">🇪🇸 ES</a>
		</div>
	</div>
</nav>

{@render children()}

<footer class="site-footer">
	<div class="content has-text-centered">
		<p class="mb-1">© 2026 Ever David Beltrán Pinto</p>

		{#if isSpanish()}
			<p class="mb-1">Computación, investigación y escritura en cultura digital.</p>
		{:else}
			<p class="mb-1">Computing, research, and writing across digital culture.</p>
		{/if}

		<p>
			<a href="mailto:edbeltranpi.chs@gmail.com">edbeltranpi.chs@gmail.com</a> ·
			<a href="https://www.linkedin.com/in/davidbeltranpinto/" target="_blank">LinkedIn</a> ·
			<a href="https://github.com/edabelt" target="_blank">GitHub</a>
		</p>
	</div>
</footer>