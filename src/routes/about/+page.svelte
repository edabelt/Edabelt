<script>
	const researchThemes = [
		{
			id: 'philosophy',
			title: 'Philosophy',
			x: 10,
			y: 20,
			z: 38,
			color: '#60796f',
			claim:
				'Ethics, epistemology, subjectivity, and aesthetics give the work its critical vocabulary.',
			question:
				'What forms of agency become possible when knowledge is organised through interfaces?',
			methods: ['critical theory', 'epistemology', 'ethics']
		},
		{
			id: 'narratology',
			title: 'Narratology',
			x: 42,
			y: 12,
			z: 68,
			color: '#8f4f3d',
			claim:
				'Narrative form, voice, perspective, plot, and temporality become computational material.',
			question: 'How do stories change when they become databases, maps, networks, and interfaces?',
			methods: ['close reading', 'narrative theory', 'cultural analysis']
		},
		{
			id: 'computation',
			title: 'Computation',
			x: 90,
			y: 22,
			z: 96,
			color: '#2e4057',
			claim:
				'Code is treated as both method and object: a way to build, test, visualise, and critique.',
			question:
				'How can computational systems make interpretation more visible rather than less human?',
			methods: ['interface design', 'data modelling', 'full-stack systems']
		},
		{
			id: 'creative-writing',
			title: 'Creative writing',
			x: 12,
			y: 62,
			z: 78,
			color: '#b0673f',
			claim:
				'Creative writing works as an experimental space for voice, memory, image, rhythm, and speculative form.',
			question:
				'How can literary invention become a method for thinking through perception, technology, and embodied experience?',
			methods: ['fiction', 'poetics', 'speculative form']
		},
		{
			id: 'digital-narrative',
			title: 'Digital narrative',
			x: 55,
			y: 62,
			z: 118,
			color: '#6f4d6f',
			claim: 'Digital narrative is where story, platform, interaction, and reader agency meet.',
			question:
				'How do interactive forms reorganise authorship, memory, sequence, and participation?',
			methods: ['interactive media', 'digital humanities', 'prototyping']
		},
		{
			id: 'digital-humanities',
			title: 'Digital humanities',
			x: 82,
			y: 78,
			z: 56,
			color: '#c89b4a',
			claim:
				'Digital humanities connects interpretive traditions with archives, platforms, metadata, and cultural memory.',
			question:
				'How can humanistic interpretation become more precise, public, and critical through digital form?',
			methods: ['archives', 'metadata', 'cultural analysis']
		},
		{
			id: 'ethics-agency',
			title: 'Ethics and agency',
			x: 30,
			y: 90,
			z: 26,
			color: '#9b5d68',
			claim:
				'Ethics and agency ask how digital systems shape responsibility, participation, and interpretation.',
			question:
				'What kinds of responsibility emerge when meaning is mediated by computational systems?',
			methods: ['ethics', 'agency', 'critical design']
		}
	];

	const themeConnections = [
		['philosophy', 'narratology'],
		['philosophy', 'digital-narrative'],
		['philosophy', 'ethics-agency'],
		['narratology', 'digital-narrative'],
		['narratology', 'creative-writing'],
		['narratology', 'computation'],
		['creative-writing', 'digital-narrative'],
		['creative-writing', 'ethics-agency'],
		['computation', 'digital-narrative'],
		['computation', 'digital-humanities'],
		['digital-narrative', 'digital-humanities'],
		['digital-humanities', 'ethics-agency'],
		['ethics-agency', 'digital-narrative']
	];

	let activeThemeId = $state('digital-narrative');
	let isResearchMapZoomed = $state(false);

	const activeTheme = $derived(
		researchThemes.find((theme) => theme.id === activeThemeId) ?? researchThemes[0]
	);

	const getTheme = (id) => researchThemes.find((theme) => theme.id === id);
	const isConnectionActive = ([source, target]) =>
		source === activeThemeId || target === activeThemeId;

	function selectResearchTheme(id) {
		activeThemeId = id;
		isResearchMapZoomed = true;
	}
</script>

<main>
	<section class="section">
		<div class="container is-max-desktop about-page">
			<h1 class="title is-2 mb-6">About</h1>

			<p>
				My work sits at the intersection of philosophy, narratology, creative writing, and
				computation. I am interested in how digital systems do more than transmit stories or
				information: they shape forms of knowledge, reorganise interpretation, and create new
				conditions for agency, memory, and meaning.
			</p>

			<p>
				My background in philosophy gives me a framework for thinking about ethics, epistemology,
				aesthetics, and subjectivity. My work in literature, narratology, and creative writing
				brings attention to form, voice, plot, perspective, atmosphere, and the cultural work
				performed by narrative structures. My training in computer science adds a practical layer:
				the ability to build, test, visualise, and critique the systems through which knowledge now
				circulates.
			</p>

			<section class="about-interactive" aria-labelledby="research-map-title">
				<div class="about-map-copy">
					<p class="landing-kicker">Research architecture</p>
					<h2 id="research-map-title">An interface for the questions behind the work.</h2>
					<p>
						This map shows the conceptual field behind my work: not separate topics, but a connected
						research practice where theory, narrative, creative invention, systems, and politics
						continually reshape each other.
					</p>
				</div>

				<div class="research-map-shell">
					<div
						class="research-network"
						class:is-zoomed={isResearchMapZoomed}
						role="presentation"
						aria-label="Interactive research map"
					>
						<div
							class="research-space"
							style={`--base-tilt: ${isResearchMapZoomed ? 50 : 58}deg; --node-counter-tilt: -${isResearchMapZoomed ? 50 : 58}deg; --map-scale: ${isResearchMapZoomed ? 0.9 : 1};`}
						>
							<div class="research-depth-floor" aria-hidden="true"></div>
							<div class="research-depth-orbit research-depth-orbit-one" aria-hidden="true"></div>
							<div class="research-depth-orbit research-depth-orbit-two" aria-hidden="true"></div>

							<svg viewBox="0 0 100 100" aria-hidden="true" class="research-network-lines">
								{#each themeConnections as connection (`${connection[0]}-${connection[1]}`)}
									{@const source = getTheme(connection[0])}
									{@const target = getTheme(connection[1])}
									{#if source && target}
										<line
											x1={source.x}
											y1={source.y}
											x2={target.x}
											y2={target.y}
											class:active={isConnectionActive(connection)}
										/>
									{/if}
								{/each}
							</svg>

							{#each researchThemes as theme (theme.id)}
								<button
									type="button"
									class="research-node"
									class:active={theme.id === activeThemeId}
									style={`--theme-color: ${theme.color}; --depth: ${theme.z}px; left: ${theme.x}%; top: ${theme.y}%;`}
									aria-pressed={theme.id === activeThemeId}
									onclick={() => selectResearchTheme(theme.id)}
									onfocus={() => selectResearchTheme(theme.id)}
								>
									<span>{theme.title}</span>
								</button>
							{/each}
						</div>
					</div>

					<aside class="research-live-panel" style={`--theme-color: ${activeTheme.color};`}>
						<span>Active concept</span>
						<h3>{activeTheme.title}</h3>
						<p>{activeTheme.claim}</p>
						<strong>{activeTheme.question}</strong>
						<div class="method-tags" aria-label="Methods">
							{#each activeTheme.methods as method (method)}
								<em>{method}</em>
							{/each}
						</div>
					</aside>
				</div>
			</section>

			<p>
				This interdisciplinary position is central to my current research direction. I am especially
				drawn to digital narrative, creative writing, computational forms of storytelling, visual
				interfaces for knowledge, and the ethical questions opened by technological systems. In this
				sense, computation is not separate from humanistic inquiry; it is one of the contemporary
				forms through which narrative, perception, agency, and knowledge are being reconfigured.
			</p>

			<p>
				Across these areas, I treat interface design as a way of thinking. Maps, networks, metadata,
				archives, textual forms, and computational models are not neutral containers; they are
				interpretive structures that shape what can be seen, compared, remembered, and questioned.
			</p>

			<p>
				Across these directions, I want to examine how narrative, creative writing, and computation
				intertwine: how stories become systems, how systems organise knowledge, and how critical
				design can reveal spaces for interpretation, memory, and ethical reflection.
			</p>
		</div>
	</section>
</main>
