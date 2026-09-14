<script>
	const capabilities = [
		'Frontends en React y SvelteKit',
		'Python y flujos de datos',
		'Filosofía y narratología',
		'Humanidades digitales críticas',
		'Mapas, gráficos y analítica visual',
		'Crítica de interfaces'
	];

	const siteNodes = [
		{
			id: 'about',
			name: 'Sobre mí',
			shortName: 'Sobre mí',
			href: '/es/about',
			x: 50,
			y: 18,
			mode: 'link',
			group: 'Identidad investigadora',
			description:
				'El centro conceptual: filosofía, narratología, computación y la forma en que el diseño de interfaces puede funcionar como análisis crítico.',
			tags: ['filosofía', 'narratología', 'computación'],
			previewTitle: 'Áreas de conocimiento',
			previews: [
				{ label: 'Filosofía, ética y epistemología', href: '/es/about' },
				{ label: 'Narratología y narrativa digital', href: '/es/about' },
				{ label: 'Computación como método crítico', href: '/es/about' }
			]
		},
		{
			id: 'projects',
			name: 'Proyectos',
			shortName: 'Proyectos',
			href: '/es/projects',
			x: 78,
			y: 38,
			mode: 'expand',
			group: 'Sistemas construidos',
			description:
				'Interfaces aplicadas, sistemas de datos y herramientas visuales donde la técnica y el diseño analítico se prueban en trabajo público.',
			tags: ['React', 'datos', 'sistemas'],
			previewTitle: 'Áreas de proyectos',
			previews: [
				{
					label: 'Cinema Atlas',
					href: '/es/projects',
					logo: '/images/projects/cinema-atlas-logo.svg'
				},
				{
					label: 'Movies App',
					href: '/es/projects',
					logo: '/images/projects/daddy-movies-logo.svg'
				},
				{
					label: 'The Wandering Desk',
					href: '/es/projects',
					logo: '/images/projects/wandering-desk-logo.svg'
				},
				{ label: 'Edabelt', href: '/es/projects', logo: '/images/projects/edabelt-logo.svg' },
				{
					label: 'WeatherTop-IoT',
					href: '/es/projects',
					logo: '/images/projects/weathertop-iot-logo.png'
				},
				{ label: 'PlaceMark', href: '/es/projects', logo: '/images/projects/placemark-logo.png' },
				{ label: 'WeatherTop', href: '/es/projects', logo: '/images/projects/weathertop-logo.png' }
			]
		},
		{
			id: 'writing',
			name: 'Escritura',
			shortName: 'Escritura',
			href: '/es/writing',
			x: 22,
			y: 40,
			mode: 'expand',
			group: 'Ensayos críticos',
			description:
				'Ensayos sobre cultura digital, conocimiento, IA, medios, evidencia y las preguntas filosóficas detrás de las interfaces.',
			tags: ['ensayos', 'cultura', 'evidencia'],
			previewTitle: 'Proyectos de escritura',
			previews: [
				{
					label: 'La revolución estética de la literatura electrónica',
					href: '/es/writing/estetica-literatura-electronica'
				},
				{
					label: 'El impacto de la tecnología en la cultura del conocimiento',
					href: '/es/writing/impacto-tecnologia-cultura-conocimiento'
				},
				{ label: 'Ética de la literatura digital', href: '/es/writing/etica-literatura-digital' },
				{
					label: 'Literatura y Conservación Cultural',
					href: '/es/writing/literature-and-culture-preservation'
				},
				{ label: 'En la isla de los Cocotuah', href: '/es/writing/en-la-isla-de-los-cocotuah' }
			]
		},
		{
			id: 'cv',
			name: 'CV',
			shortName: 'CV',
			href: '/es/cv',
			x: 24,
			y: 76,
			mode: 'link',
			group: 'Trayectoria',
			description:
				'Formación, habilidades, proyectos y experiencia organizados como una trayectoria de investigación y desarrollo.',
			tags: ['formación', 'habilidades', 'experiencia'],
			previewTitle: 'Secciones del CV',
			previews: [
				{ label: 'Perfil investigador y formación', href: '/es/cv' },
				{ label: 'Proyectos técnicos seleccionados', href: '/es/cv' },
				{ label: 'Habilidades, idiomas y experiencia', href: '/es/cv' }
			]
		},
		{
			id: 'leisure',
			name: 'Ocio',
			shortName: 'Ocio',
			href: '/es/leisure',
			x: 50,
			y: 88,
			mode: 'link',
			group: 'Práctica encarnada',
			description:
				'Ajedrez, baile, gimnasio y chess boxing como prácticas de atención, ritmo, disciplina y presión táctica fuera de la investigación formal.',
			tags: ['estrategia', 'cuerpo', 'disciplina'],
			previewTitle: 'Prácticas de ocio',
			previews: [
				{ label: 'Ajedrez como patrón y paciencia', href: '/es/leisure' },
				{ label: 'Baile como temporalidad encarnada', href: '/es/leisure' },
				{ label: 'Gimnasio y chess boxing como disciplina', href: '/es/leisure' }
			]
		},
		{
			id: 'contact',
			name: 'Contacto',
			shortName: 'Contacto',
			href: '/es/contact',
			x: 76,
			y: 74,
			mode: 'link',
			group: 'Conversación',
			description:
				'Una ruta directa para colaboraciones, conversaciones de investigación y trabajo que conecte práctica computacional e interpretación.',
			tags: ['colaboración', 'investigación', 'trabajo'],
			previewTitle: 'Rutas de contacto',
			previews: [
				{ label: 'Colaboración investigadora', href: '/es/contact' },
				{ label: 'Trabajo técnico y de interfaces', href: '/es/contact' },
				{ label: 'Conversaciones editoriales o de escritura', href: '/es/contact' }
			]
		}
	];

	const siteConnections = [
		{ from: 'about', to: 'writing', label: 'áreas de investigación desarrolladas en ensayos' },
		{ from: 'about', to: 'projects', label: 'intereses de investigación llevados a interfaces' },
		{ from: 'projects', to: 'cv', label: 'trabajo construido junto a habilidades y formación' },
		{ from: 'writing', to: 'cv', label: 'formación académica detrás de la escritura' },
		{ from: 'about', to: 'leisure', label: 'atención y cuerpo más allá de la investigación' },
		{ from: 'leisure', to: 'cv', label: 'disciplina y práctica detrás del perfil' },
		{ from: 'projects', to: 'contact', label: 'proyectos que pueden abrir colaboración' },
		{ from: 'writing', to: 'contact', label: 'conversaciones de investigación y edición' },
		{ from: 'leisure', to: 'contact', label: 'prácticas personales detrás de la colaboración' },
		{ from: 'cv', to: 'contact', label: 'perfil profesional y contacto directo' }
	];

	let activeSiteNodeId = $state('writing');

	const activeSiteNode = $derived(
		siteNodes.find((node) => node.id === activeSiteNodeId) ?? siteNodes[0]
	);

	function getSiteNode(id) {
		return siteNodes.find((node) => node.id === id);
	}

	function isSiteConnectionActive(connection) {
		return connection.from === activeSiteNodeId || connection.to === activeSiteNodeId;
	}

	function isExpandableNode(node) {
		return node.mode === 'expand';
	}

	let isLandingPortraitOpen = $state(false);

	function handlePortraitKeydown(event) {
		if (event.key === 'Escape') {
			isLandingPortraitOpen = false;
		}
	}

	function closePortraitFromBackdrop(event) {
		if (event.target === event.currentTarget) {
			isLandingPortraitOpen = false;
		}
	}
</script>

<svelte:window onkeydown={handlePortraitKeydown} />

<main>
	<section class="landing-hero">
		<div class="landing-shell">
			<div class="hero-copy-block">
				<p class="landing-kicker">
					Filosofía · Narratología · Humanidades Digitales · Computación · Interfaces Analíticas
				</p>
				<h1>Ever David Beltrán Pinto</h1>
				<div class="landing-portrait-lockup">
					<button
						type="button"
						class="landing-portrait-trigger"
						aria-label="Ver retrato ampliado de Ever David Beltrán Pinto"
						onclick={() => (isLandingPortraitOpen = true)}
					>
						<img
							src="/images/ever-beltran-portrait-blurred.jpg"
							alt="Retrato de Ever David Beltrán Pinto"
						/>
					</button>
					<p>Investigador y desarrollador entre interpretación crítica y sistemas visuales.</p>
				</div>
				<p class="landing-lede">
					Construyo sistemas visuales y analíticos como forma de investigación crítica: interfaces
					donde mapas, redes, estructuras narrativas y evidencia ayudan a interpretar cómo la
					cultura digital organiza conocimiento, agencia y sentido.
				</p>

				<div class="landing-capabilities" aria-label="Capacidades técnicas">
					{#each capabilities as capability (capability)}
						<span>{capability}</span>
					{/each}
				</div>
			</div>

			<div class="site-map-explorer" aria-label="Mapa interactivo del sitio">
				<div class="site-map-toolbar">
					<span>Mapa Interactivo del Sitio</span>
					<span>{activeSiteNode.group}</span>
				</div>

				<div class="site-map-body">
					<div class="site-network">
						<div class="network-legend">
							<span>Ruta activa</span>
							<span>Sitio como mapa de investigación</span>
						</div>

						<svg class="site-network-lines" viewBox="0 0 100 100" aria-hidden="true">
							{#each siteConnections as connection (`${connection.from}-${connection.to}`)}
								{@const source = getSiteNode(connection.from)}
								{@const target = getSiteNode(connection.to)}
								{#if source && target}
									<line
										class:active={isSiteConnectionActive(connection)}
										x1={source.x}
										y1={source.y}
										x2={target.x}
										y2={target.y}
									></line>
								{/if}
							{/each}
						</svg>

						{#each siteNodes as node (node.id)}
							{#if isExpandableNode(node)}
								<button
									type="button"
									class="site-node"
									class:active={node.id === activeSiteNodeId}
									style={`left: ${node.x}%; top: ${node.y}%;`}
									aria-pressed={node.id === activeSiteNodeId}
									onclick={() => (activeSiteNodeId = node.id)}
								>
									<span>{node.shortName}</span>
								</button>
							{:else}
								<a
									class="site-node is-link"
									href={node.href}
									style={`left: ${node.x}%; top: ${node.y}%;`}
									aria-label={`Abrir ${node.name}`}
								>
									<span>{node.shortName}</span>
								</a>
							{/if}
						{/each}
					</div>

					<aside class="site-node-panel" aria-live="polite">
						<p class="panel-eyebrow">Colección interactiva</p>
						<p class="project-type">{activeSiteNode.group}</p>
						<h2>{activeSiteNode.name}</h2>
						<p>{activeSiteNode.description}</p>

						<div class="site-node-tags">
							{#each activeSiteNode.tags as tag (tag)}
								<span>{tag}</span>
							{/each}
						</div>

						<div class="site-node-connections">
							<p>Enlaces entre páginas</p>
							{#each siteConnections.filter(isSiteConnectionActive) as connection (`${connection.from}-${connection.to}`)}
								<span>{connection.label}</span>
							{/each}
						</div>

						<div class="site-node-previews">
							<p>{activeSiteNode.previewTitle}</p>
							{#each activeSiteNode.previews as preview (preview.label)}
								<a href={preview.href}>
									{#if preview.logo}
										<img src={preview.logo} alt="" loading="lazy" />
									{/if}
									<span>{preview.label}</span>
								</a>
							{/each}
						</div>

						<a class="button is-light" href={activeSiteNode.href}>Leer más</a>
					</aside>
				</div>
			</div>
		</div>
	</section>

	{#if isLandingPortraitOpen}
		<div
			class="cv-portrait-lightbox"
			role="dialog"
			aria-modal="true"
			aria-label="Vista ampliada del retrato"
			tabindex="-1"
			onclick={closePortraitFromBackdrop}
			onkeydown={handlePortraitKeydown}
		>
			<div class="cv-portrait-preview">
				<button type="button" onclick={() => (isLandingPortraitOpen = false)}>Cerrar</button>
				<img src="/images/ever-beltran-portrait-blurred.jpg" alt="Ever David Beltrán Pinto" />
			</div>
		</div>
	{/if}
</main>
