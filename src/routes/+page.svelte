<script>
	const capabilities = [
		'React and SvelteKit frontends',
		'Python and data workflows',
		'Philosophy and narratology',
		'Critical digital humanities',
		'Maps, charts, and visual analytics',
		'Research-led interface critique'
	];

	const siteNodes = [
		{
			id: 'about',
			name: 'About',
			shortName: 'About',
			href: '/about',
			x: 50,
			y: 18,
			mode: 'link',
			group: 'Research identity',
			description:
				'The conceptual centre: philosophy, narratology, computation, and the way interface design becomes a method for critical analysis.',
			tags: ['philosophy', 'narratology', 'computation'],
			previewTitle: 'Knowledge areas',
			previews: [
				{ label: 'Philosophy, ethics, and epistemology', href: '/about' },
				{ label: 'Narratology and digital narrative', href: '/about' },
				{ label: 'Computation as critical method', href: '/about' }
			]
		},
		{
			id: 'projects',
			name: 'Projects',
			shortName: 'Projects',
			href: '/projects',
			x: 78,
			y: 38,
			mode: 'expand',
			group: 'Built systems',
			description:
				'Applied interfaces, data systems, and visual tools where technical craft and analytical design are tested in public-facing work.',
			tags: ['React', 'data UI', 'systems'],
			previewTitle: 'Project areas',
			previews: [
				{
					label: 'Cinema Atlas',
					href: '/projects',
					logo: '/images/projects/cinema-atlas-logo.svg'
				},
				{ label: 'Movies App', href: '/projects', logo: '/images/projects/daddy-movies-logo.svg' },
				{
					label: 'The Wandering Desk',
					href: '/projects',
					logo: '/images/projects/wandering-desk-logo.svg'
				},
				{ label: 'Edabelt', href: '/projects', logo: '/images/projects/edabelt-logo.svg' },
				{
					label: 'WeatherTop-IoT',
					href: '/projects',
					logo: '/images/projects/weathertop-iot-logo.png'
				},
				{ label: 'PlaceMark', href: '/projects', logo: '/images/projects/placemark-logo.png' },
				{ label: 'WeatherTop', href: '/projects', logo: '/images/projects/weathertop-logo.png' }
			]
		},
		{
			id: 'writing',
			name: 'Writing',
			shortName: 'Writing',
			href: '/writing',
			x: 22,
			y: 40,
			mode: 'expand',
			group: 'Critical essays',
			description:
				'Essays on digital culture, knowledge, AI, media, evidence, and the philosophical questions behind interfaces.',
			tags: ['essays', 'culture', 'evidence'],
			previewTitle: 'Writing projects',
			previews: [
				{
					label: 'The Aesthetic Revolution of Electronic Literature',
					href: '/writing/estetica-literatura-electronica'
				},
				{
					label: 'The Impact of Technology on Knowledge Culture',
					href: '/writing/impacto-tecnologia-cultura-conocimiento'
				},
				{ label: 'Ethics of Digital Literature', href: '/writing/etica-literatura-digital' },
				{
					label: 'Literature and Cultural Preservation',
					href: '/writing/literature-and-culture-preservation'
				},
				{ label: 'On the Island of the Cocotuah', href: '/writing/en-la-isla-de-los-cocotuah' }
			]
		},
		{
			id: 'cv',
			name: 'CV',
			shortName: 'CV',
			href: '/cv',
			x: 24,
			y: 76,
			mode: 'link',
			group: 'Trajectory',
			description:
				'Education, skills, projects, and experience organised as a research and development path rather than a flat credential list.',
			tags: ['education', 'skills', 'experience'],
			previewTitle: 'CV sections',
			previews: [
				{ label: 'Research profile and education', href: '/cv' },
				{ label: 'Selected technical projects', href: '/cv' },
				{ label: 'Skills, languages, and experience', href: '/cv' }
			]
		},
		{
			id: 'leisure',
			name: 'Leisure',
			shortName: 'Leisure',
			href: '/leisure',
			x: 50,
			y: 88,
			mode: 'link',
			group: 'Embodied practice',
			description:
				'Chess, dancing, gym training, and chess boxing as practices of attention, rhythm, discipline, and tactical pressure outside formal research.',
			tags: ['strategy', 'body', 'discipline'],
			previewTitle: 'Leisure practices',
			previews: [
				{ label: 'Chess as pattern and patience', href: '/leisure' },
				{ label: 'Dancing as embodied timing', href: '/leisure' },
				{ label: 'Gym and chess boxing as discipline', href: '/leisure' }
			]
		},
		{
			id: 'contact',
			name: 'Contact',
			shortName: 'Contact',
			href: '/contact',
			x: 76,
			y: 74,
			mode: 'link',
			group: 'Conversation',
			description:
				'A direct path for collaborations, research conversations, and work that connects computational practice with interpretation.',
			tags: ['collaboration', 'research', 'work'],
			previewTitle: 'Contact paths',
			previews: [
				{ label: 'Research collaboration', href: '/contact' },
				{ label: 'Technical and interface work', href: '/contact' },
				{ label: 'Editorial or writing conversations', href: '/contact' }
			]
		}
	];

	const siteConnections = [
		{ from: 'about', to: 'writing', label: 'research areas expanded as essays' },
		{ from: 'about', to: 'projects', label: 'research interests translated into interfaces' },
		{ from: 'projects', to: 'cv', label: 'built work listed with skills and education' },
		{ from: 'writing', to: 'cv', label: 'academic formation behind the written work' },
		{ from: 'about', to: 'leisure', label: 'attention and embodiment beyond research pages' },
		{ from: 'leisure', to: 'cv', label: 'discipline and practice behind the profile' },
		{ from: 'projects', to: 'contact', label: 'project work that can become collaboration' },
		{ from: 'writing', to: 'contact', label: 'research and editorial conversations' },
		{ from: 'leisure', to: 'contact', label: 'personal practices behind collaboration' },
		{ from: 'cv', to: 'contact', label: 'professional profile and direct contact' }
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
					Philosophy · Narratology · Digital Humanities · Computation · Analytical Interfaces
				</p>
				<h1>Ever David Beltrán Pinto</h1>
				<div class="landing-portrait-lockup">
					<button
						type="button"
						class="landing-portrait-trigger"
						aria-label="View larger portrait of Ever David Beltrán Pinto"
						onclick={() => (isLandingPortraitOpen = true)}
					>
						<img
							src="/images/ever-beltran-portrait-blurred.jpg"
							alt="Portrait of Ever David Beltrán Pinto"
						/>
					</button>
					<p>
						Researcher and developer working between critical interpretation and visual systems.
					</p>
				</div>
				<p class="landing-lede">
					I build visual and analytical systems as a form of critical inquiry: interfaces where
					maps, networks, narrative structures, and evidence help interpret how digital culture
					organises knowledge, agency, and meaning.
				</p>

				<div class="landing-capabilities" aria-label="Technical capabilities">
					{#each capabilities as capability (capability)}
						<span>{capability}</span>
					{/each}
				</div>
			</div>

			<div class="site-map-explorer" aria-label="Interactive map of the site">
				<div class="site-map-toolbar">
					<span>Interactive Site Map</span>
					<span>{activeSiteNode.group}</span>
				</div>

				<div class="site-map-body">
					<div class="site-network">
						<div class="network-legend">
							<span>Active path</span>
							<span>Site as research map</span>
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
									aria-label={`Open ${node.name}`}
								>
									<span>{node.shortName}</span>
								</a>
							{/if}
						{/each}
					</div>

					<aside class="site-node-panel" aria-live="polite">
						<p class="panel-eyebrow">Interactive collection</p>
						<p class="project-type">{activeSiteNode.group}</p>
						<h2>{activeSiteNode.name}</h2>
						<p>{activeSiteNode.description}</p>

						<div class="site-node-tags">
							{#each activeSiteNode.tags as tag (tag)}
								<span>{tag}</span>
							{/each}
						</div>

						<div class="site-node-connections">
							<p>Page links</p>
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

						<a class="button is-light" href={activeSiteNode.href}>Read more</a>
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
			aria-label="Portrait preview"
			tabindex="-1"
			onclick={closePortraitFromBackdrop}
			onkeydown={handlePortraitKeydown}
		>
			<div class="cv-portrait-preview">
				<button type="button" onclick={() => (isLandingPortraitOpen = false)}>Close</button>
				<img src="/images/ever-beltran-portrait-blurred.jpg" alt="Ever David Beltrán Pinto" />
			</div>
		</div>
	{/if}
</main>
