<script>
	const researchThemes = [
		{
			id: 'philosophy',
			title: 'Filosofía',
			x: 10,
			y: 20,
			z: 38,
			color: '#60796f',
			claim:
				'La ética, la epistemología, la subjetividad y la estética le dan al trabajo su vocabulario crítico.',
			question:
				'¿Qué formas de agencia aparecen cuando el conocimiento se organiza mediante interfaces?',
			methods: ['teoría crítica', 'epistemología', 'ética']
		},
		{
			id: 'narratology',
			title: 'Narratología',
			x: 42,
			y: 12,
			z: 68,
			color: '#8f4f3d',
			claim:
				'La forma narrativa, la voz, la perspectiva, la trama y la temporalidad se vuelven material computacional.',
			question:
				'¿Cómo cambian las historias cuando se convierten en bases de datos, mapas, redes e interfaces?',
			methods: ['lectura cercana', 'teoría narrativa', 'análisis cultural']
		},
		{
			id: 'computation',
			title: 'Computación',
			x: 90,
			y: 22,
			z: 96,
			color: '#2e4057',
			claim:
				'El código funciona como método y objeto: una forma de construir, probar, visualizar y criticar.',
			question:
				'¿Cómo pueden los sistemas computacionales hacer más visible la interpretación, no menos humana?',
			methods: ['diseño de interfaces', 'modelado de datos', 'sistemas full-stack']
		},
		{
			id: 'creative-writing',
			title: 'Escritura creativa',
			x: 12,
			y: 62,
			z: 78,
			color: '#b0673f',
			claim:
				'La escritura creativa funciona como un espacio experimental para la voz, la memoria, la imagen, el ritmo y la forma especulativa.',
			question:
				'¿Cómo puede la invención literaria volverse un método para pensar percepción, tecnología y experiencia corporal?',
			methods: ['ficción', 'poética', 'forma especulativa']
		},
		{
			id: 'digital-narrative',
			title: 'Narrativa digital',
			x: 55,
			y: 62,
			z: 118,
			color: '#6f4d6f',
			claim:
				'La narrativa digital es el punto donde se encuentran historia, plataforma, interacción y agencia lectora.',
			question:
				'¿Cómo reorganizan las formas interactivas la autoría, la memoria, la secuencia y la participación?',
			methods: ['medios interactivos', 'humanidades digitales', 'prototipado']
		},
		{
			id: 'digital-humanities',
			title: 'Humanidades digitales',
			x: 82,
			y: 78,
			z: 56,
			color: '#c89b4a',
			claim:
				'Las humanidades digitales conectan tradiciones interpretativas con archivos, plataformas, metadatos y memoria cultural.',
			question:
				'¿Cómo puede la interpretación humanística volverse más precisa, pública y crítica mediante formas digitales?',
			methods: ['archivos', 'metadatos', 'análisis cultural']
		},
		{
			id: 'ethics-agency',
			title: 'Ética y agencia',
			x: 30,
			y: 90,
			z: 26,
			color: '#9b5d68',
			claim:
				'La ética y la agencia preguntan cómo los sistemas digitales configuran responsabilidad, participación e interpretación.',
			question:
				'¿Qué responsabilidades aparecen cuando el sentido está mediado por sistemas computacionales?',
			methods: ['ética', 'agencia', 'diseño crítico']
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
			<h1 class="title is-2 mb-6">Sobre mí</h1>

			<p>
				Mi trabajo se sitúa en la intersección entre filosofía, narratología, escritura creativa y
				computación. Me interesa cómo los sistemas digitales no solo transmiten historias o
				información, sino que configuran formas de conocimiento, reorganizan la interpretación y
				crean nuevas condiciones para la agencia, la memoria y la producción de sentido.
			</p>

			<p>
				Mi formación filosófica me permite pensar cuestiones de ética, epistemología, estética y
				subjetividad. Mi trabajo en literatura, narratología y escritura creativa aporta atención a
				la forma, la voz, la trama, la perspectiva, la atmósfera y el trabajo cultural de las
				estructuras narrativas. Mi formación en ciencias de la computación añade una capa práctica:
				la capacidad de construir, probar, visualizar y criticar los sistemas por los que hoy
				circula el conocimiento.
			</p>

			<section class="about-interactive" aria-labelledby="research-map-title">
				<div class="about-map-copy">
					<p class="landing-kicker">Arquitectura de investigación</p>
					<h2 id="research-map-title">Una interfaz para las preguntas detrás del trabajo.</h2>
					<p>
						Este mapa muestra el campo conceptual detrás de mi trabajo: no temas separados, sino una
						práctica investigadora conectada donde teoría, narrativa, invención creativa, sistemas y
						política se transforman mutuamente.
					</p>
				</div>

				<div class="research-map-shell">
					<div
						class="research-network"
						class:is-zoomed={isResearchMapZoomed}
						role="presentation"
						aria-label="Mapa interactivo de investigación"
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
						<span>Concepto activo</span>
						<h3>{activeTheme.title}</h3>
						<p>{activeTheme.claim}</p>
						<strong>{activeTheme.question}</strong>
						<div class="method-tags" aria-label="Métodos">
							{#each activeTheme.methods as method (method)}
								<em>{method}</em>
							{/each}
						</div>
					</aside>
				</div>
			</section>

			<p>
				Esta posición interdisciplinar define mi orientación investigadora actual. Me interesan
				especialmente la narrativa digital, la escritura creativa, las formas computacionales de
				contar, las interfaces visuales para el conocimiento y las preguntas éticas abiertas por los
				sistemas tecnológicos. En este sentido, la computación no está separada de la investigación
				humanística: es una de las formas contemporáneas mediante las cuales se reconfiguran
				narrativa, percepción, agencia y conocimiento.
			</p>

			<p>
				En estas áreas, entiendo el diseño de interfaces como una forma de pensamiento. Mapas,
				redes, metadatos, archivos, formas textuales y modelos computacionales no son contenedores
				neutrales; son estructuras interpretativas que configuran lo que puede verse, compararse,
				recordarse y cuestionarse.
			</p>

			<p>
				En esas líneas busco estudiar cómo narrativa, escritura creativa y computación se
				entrelazan: cómo las historias se convierten en sistemas, cómo los sistemas organizan
				conocimiento y cómo el diseño crítico puede revelar espacios de interpretación, memoria y
				reflexión ética.
			</p>
		</div>
	</section>
</main>
