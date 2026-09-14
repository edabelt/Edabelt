<script>
	const atlasSteps = ['Mundo', 'País', 'Género', 'Tema', 'Película'];
	const atlasCountries = [
		'Estados Unidos',
		'Brasil',
		'Reino Unido',
		'Alemania',
		'Suecia',
		'Sudáfrica',
		'India',
		'Corea del Sur',
		'Australia'
	];
	const atlasGenres = ['Drama', 'Documental', 'Thriller', 'Ciencia ficción'];
	const atlasThemes = ['Migración', 'Memoria', 'Vida urbana', 'Resistencia'];
	const atlasFilms = ['Moonlight', 'Ciudad de Dios', 'Parasite', 'Retrato de una mujer en llamas'];

	let atlasStep = $state(0);
	let selectedCountry = $state('');
	let selectedGenre = $state('');
	let selectedTheme = $state('');
	let selectedFilm = $state('');

	const atlasHeading = $derived(
		atlasStep === 0
			? 'Selecciona un país productor de cine'
			: atlasStep === 1
				? `Explora géneros en ${selectedCountry}`
				: atlasStep === 2
					? `${selectedGenre} como paisaje cinematográfico`
					: atlasStep === 3
						? `${selectedTheme} a través de películas`
						: `${selectedFilm} como evidencia`
	);

	const atlasCopy = $derived(
		atlasStep === 0
			? 'Avanza desde la vista global hacia géneros, temas y películas individuales.'
			: atlasStep === 1
				? 'Elige un género para acotar el campo cultural y cinematográfico.'
				: atlasStep === 2
					? 'Sigue indicadores temáticos que conectan películas más allá de una categoría.'
					: atlasStep === 3
						? 'Selecciona una película para llegar a la capa de evidencia.'
						: 'Una película se convierte en nodo dentro de un mapa más amplio de lugar, género y tema.'
	);

	function chooseCountry(country) {
		selectedCountry = country;
		selectedGenre = '';
		selectedTheme = '';
		selectedFilm = '';
		atlasStep = 1;
	}

	function chooseGenre(genre) {
		selectedGenre = genre;
		selectedTheme = '';
		selectedFilm = '';
		atlasStep = 2;
	}

	function chooseTheme(theme) {
		selectedTheme = theme;
		selectedFilm = '';
		atlasStep = 3;
	}

	function chooseFilm(film) {
		selectedFilm = film;
		atlasStep = 4;
	}

	function resetAtlasFlow() {
		atlasStep = 0;
		selectedCountry = '';
		selectedGenre = '';
		selectedTheme = '';
		selectedFilm = '';
	}
</script>

<main>
	<section class="section">
		<div class="container is-max-desktop project-page">
			<p class="is-size-7 has-text-grey mb-3">Trabajo técnico seleccionado</p>
			<h1 class="title is-2 mb-5">Proyectos</h1>

			<p class="writing-intro">
				Selección de proyectos en desarrollo web, analítica visual, integración de APIs y diseño de
				interfaces orientadas a datos. Mi trabajo técnico se centra en sistemas que hacen la
				información explorable, verificable y útil.
			</p>

			<section class="cinema-atlas-entry" aria-labelledby="cinema-atlas-entry-title">
				<div class="cinema-cover-content">
					<span class="cinema-cover-kicker">Atlas interactivo de cine</span>
					<h2 id="cinema-atlas-entry-title">
						Mapa mundial → país → género → tema → evidencia fílmica
					</h2>
					<p>
						Una interfaz pública de investigación donde los metadatos fílmicos se vuelven geografía,
						tendencias y constelaciones temáticas.
					</p>
					<a
						href="https://cinemaatlas-bfepyveka-edabelt.vercel.app/"
						target="_blank"
						rel="noopener noreferrer">Abrir demo en vivo</a
					>
				</div>
				<div class="cinema-atlas-preview">
					<div class="atlas-toolbar">
						<span>Cinema Atlas</span>
						<span>Modo mapa · Ruta de evidencia</span>
					</div>
					<div class="interface-status-row">
						{#each atlasSteps as step, index}
							<button
								type="button"
								class:is-active={atlasStep === index}
								disabled={index > atlasStep}
								onclick={() => (atlasStep = index)}
							>
								{step}
							</button>
						{/each}
					</div>
					<div class="atlas-stage-card">
						<h3>{atlasHeading}</h3>
						<p>{atlasCopy}</p>
						<svg class="atlas-map" viewBox="0 0 760 360" aria-hidden="true">
							<rect width="760" height="360" rx="12" />
							<g class="atlas-grid">
								<line x1="70" y1="42" x2="70" y2="318" />
								<line x1="180" y1="42" x2="180" y2="318" />
								<line x1="290" y1="42" x2="290" y2="318" />
								<line x1="400" y1="42" x2="400" y2="318" />
								<line x1="510" y1="42" x2="510" y2="318" />
								<line x1="620" y1="42" x2="620" y2="318" />
								<line x1="34" y1="100" x2="724" y2="100" />
								<line x1="34" y1="180" x2="724" y2="180" />
								<line x1="34" y1="260" x2="724" y2="260" />
							</g>
							<g class="atlas-land">
								<path
									d="M76 112 L104 82 L154 70 L205 92 L224 128 L194 150 L183 190 L154 220 L126 198 L138 160 L104 148 Z"
								/>
								<path d="M198 210 L238 226 L264 262 L252 312 L220 330 L190 300 L172 252 Z" />
								<path d="M332 102 L382 78 L442 94 L456 132 L420 154 L362 146 Z" />
								<path d="M382 160 L432 148 L474 180 L492 236 L460 302 L414 270 L390 218 Z" />
								<path d="M470 92 L542 72 L644 98 L704 152 L670 206 L584 190 L520 222 L482 178 Z" />
								<path d="M594 260 L650 246 L690 282 L664 318 L604 314 Z" />
							</g>
							<g class="atlas-country-highlights">
								<circle class:active={atlasStep > 0} cx="158" cy="134" r="12" />
								<circle class:active={atlasStep > 0} cx="226" cy="252" r="10" />
								<circle class:active={atlasStep > 0} cx="385" cy="116" r="8" />
								<circle class:active={atlasStep > 0} cx="500" cy="190" r="10" />
								<circle class:active={atlasStep > 0} cx="635" cy="288" r="12" />
							</g>
							<path class="map-line muted" d="M142 142 C222 84 318 96 390 150 S548 238 646 192" />
							<path class="atlas-route" d="M174 158 C248 210 338 218 430 172 S566 132 640 198" />
							<g class="atlas-nodes">
								<circle cx="174" cy="158" r="11" />
								<circle cx="332" cy="212" r="9" />
								<circle cx="430" cy="172" r="12" />
								<circle cx="640" cy="198" r="10" />
							</g>
						</svg>
						<div class="atlas-choice-panel">
							<span>
								{atlasStep === 0
									? 'Países disponibles'
									: atlasStep === 1
										? 'Géneros disponibles'
										: atlasStep === 2
											? 'Indicadores temáticos'
											: atlasStep === 3
												? 'Evidencia fílmica'
												: 'Ruta seleccionada'}
							</span>
							<div class="atlas-choice-grid">
								{#if atlasStep === 0}
									{#each atlasCountries as country}
										<button type="button" onclick={() => chooseCountry(country)}>{country}</button>
									{/each}
								{:else if atlasStep === 1}
									{#each atlasGenres as genre}
										<button type="button" onclick={() => chooseGenre(genre)}>{genre}</button>
									{/each}
								{:else if atlasStep === 2}
									{#each atlasThemes as theme}
										<button type="button" onclick={() => chooseTheme(theme)}>{theme}</button>
									{/each}
								{:else if atlasStep === 3}
									{#each atlasFilms as film}
										<button type="button" onclick={() => chooseFilm(film)}>{film}</button>
									{/each}
								{:else}
									<button type="button" onclick={resetAtlasFlow}>Reiniciar ruta</button>
								{/if}
							</div>
						</div>
					</div>
				</div>
			</section>

			<section class="featured-projects" aria-labelledby="featured-projects-title">
				<h2 id="featured-projects-title" class="title is-4">Trabajo Destacado</h2>

				<div class="columns is-variable is-5 is-multiline">
					<div class="column is-half">
						<article class="card project-card project-card-featured">
							<div class="card-content">
								<a
									class="project-card-cover"
									href="https://cinemaatlas-bfepyveka-edabelt.vercel.app/"
									target="_blank"
									rel="noopener noreferrer"
									aria-label="Abrir demo en vivo de Cinema Atlas"
								>
									<img src="/images/projects/cinema-atlas-logo.svg" alt="" />
									<span class="project-cover-label">Mapa · Cine · Evidencia</span>
								</a>
								<p class="project-meta">React · TypeScript · D3 · ECharts</p>
								<h3 class="title is-4">Cinema Atlas</h3>

								<p>
									Analítica visual interactiva de cine que avanza desde un mapa mundial hacia país,
									género, tema y evidencia fílmica individual. El proyecto combina metadatos de
									TMDB, geografía con D3, tendencias con ECharts y constelaciones temáticas en una
									interfaz pública de investigación.
								</p>

								<div class="tags mt-4">
									<span class="tag is-light">Analítica visual</span>
									<span class="tag is-light">Humanidades digitales</span>
									<span class="tag is-light">TMDB API</span>
								</div>

								<p class="project-links">
									<a
										href="https://github.com/edabelt/Cinema-Atlas"
										target="_blank"
										rel="noopener noreferrer"
									>
										GitHub
									</a>
									·
									<a
										href="https://cinemaatlas-bfepyveka-edabelt.vercel.app/"
										target="_blank"
										rel="noopener noreferrer"
									>
										Demo en vivo
									</a>
								</p>
							</div>
						</article>
					</div>

					<div class="column is-half">
						<article class="card project-card project-card-featured">
							<div class="card-content">
								<a
									class="project-card-cover"
									href="https://daddymovies.vercel.app/movies/upcoming"
									target="_blank"
									rel="noopener noreferrer"
									aria-label="Abrir demo en vivo de Movies App"
								>
									<img src="/images/projects/daddy-movies-logo.svg" alt="" />
									<span class="project-cover-label">Descubrimiento · Playlists</span>
								</a>
								<p class="project-meta">React · Supabase · React Query · Material UI</p>
								<h3 class="title is-4">Movies App</h3>

								<p>
									Plataforma de descubrimiento de películas con exploración, filtros, próximos
									estrenos, páginas de actores, autenticación, favoritos, playlists y reseñas.
									Funciona como la capa de producto alrededor de Cinema Atlas y conecta registros
									fílmicos con flujos de usuario.
								</p>

								<div class="tags mt-4">
									<span class="tag is-light">Frontend full-stack</span>
									<span class="tag is-light">Autenticación</span>
									<span class="tag is-light">Playlists</span>
								</div>

								<p class="project-links">
									<a
										href="https://github.com/edabelt/Cinema-Atlas"
										target="_blank"
										rel="noopener noreferrer"
									>
										GitHub
									</a>
									·
									<a
										href="https://daddymovies.vercel.app/movies/upcoming"
										target="_blank"
										rel="noopener noreferrer"
									>
										Demo en vivo
									</a>
								</p>
							</div>
						</article>
					</div>
				</div>
			</section>

			<section class="project-grid" aria-labelledby="more-projects-title">
				<h2 id="more-projects-title" class="title is-4">Otros Proyectos</h2>

				<div class="columns is-multiline is-variable is-5">
					<div class="column is-half">
						<article class="card project-card">
							<div class="card-content">
								<a
									class="project-card-cover project-card-cover-compact"
									href="https://edabelt.netlify.app/"
									target="_blank"
									rel="noopener noreferrer"
									aria-label="Abrir demo en vivo de Edabelt"
								>
									<img src="/images/projects/edabelt-logo.svg" alt="" />
									<span class="project-cover-label">Portafolio · Investigación · Escritura</span>
								</a>
								<p class="project-meta">SvelteKit · Bulma · Portfolio</p>
								<h3 class="title is-5">Edabelt</h3>
								<p>
									Sitio personal desarrollado con SvelteKit y Bulma para integrar escritura,
									investigación y desarrollo en una arquitectura web ligera y bilingüe.
								</p>
								<p class="project-links">
									<a
										href="https://github.com/edabelt/Edabelt"
										target="_blank"
										rel="noopener noreferrer">GitHub</a
									>
									·
									<a href="https://edabelt.netlify.app/" target="_blank" rel="noopener noreferrer"
										>Demo en vivo</a
									>
								</p>
							</div>
						</article>
					</div>

					<div class="column is-half">
						<article class="card project-card">
							<div class="card-content">
								<a
									class="project-card-cover project-card-cover-compact"
									href="https://thewanderingdesk.netlify.app/"
									target="_blank"
									rel="noopener noreferrer"
									aria-label="Abrir demo en vivo de The Wandering Desk"
								>
									<span class="project-card-wordmark">The Wandering Desk</span>
									<span class="project-cover-label">Frontend · Backend · API</span>
								</a>
								<p class="project-meta">Multi-repo · Full-stack · Arquitectura API</p>
								<h3 class="title is-5">The Wandering Desk</h3>
								<p>
									Proyecto full-stack dividido en repositorios dedicados para frontend, backend y
									API, estructurado como una aplicación modular con separación clara entre interfaz,
									lógica de servidor y acceso a datos.
								</p>
								<p class="project-links">
									<a
										href="https://thewanderingdesk.netlify.app/"
										target="_blank"
										rel="noopener noreferrer">Demo en vivo</a
									>
									·
									<a
										href="https://github.com/edabelt/thewanderingdesk-frontend"
										target="_blank"
										rel="noopener noreferrer">Frontend</a
									>
									·
									<a
										href="https://github.com/edabelt/thewanderingdesk-backend"
										target="_blank"
										rel="noopener noreferrer">Backend</a
									>
									·
									<a
										href="https://github.com/edabelt/thewanderingdesk-api"
										target="_blank"
										rel="noopener noreferrer">API</a
									>
								</p>
							</div>
						</article>
					</div>

					<div class="column is-half">
						<article class="card project-card">
							<div class="card-content">
								<a
									class="project-card-cover project-card-cover-compact"
									href="https://weathertop-iot.onrender.com/"
									target="_blank"
									rel="noopener noreferrer"
									aria-label="Abrir demo en vivo de WeatherTop-IoT"
								>
									<img src="/images/projects/weathertop-iot-logo.png" alt="" />
									<span class="project-cover-label">Telemetría · MQTT · Dispositivos</span>
								</a>
								<p class="project-meta">IoT · Node.js · MQTT</p>
								<h3 class="title is-5">WeatherTop-IoT</h3>
								<p>
									Sistema orientado a eventos para procesamiento de telemetría en tiempo real con
									MQTT, backend en Node.js y visualización de datos.
								</p>
								<p class="project-links">
									<a
										href="https://github.com/edabelt/WeatherTop-iot"
										target="_blank"
										rel="noopener noreferrer">GitHub</a
									>
									·
									<a
										href="https://weathertop-iot.onrender.com/"
										target="_blank"
										rel="noopener noreferrer">Demo en vivo</a
									>
								</p>
							</div>
						</article>
					</div>

					<div class="column is-half">
						<article class="card project-card">
							<div class="card-content">
								<a
									class="project-card-cover project-card-cover-compact"
									href="https://placemark-a2vl.onrender.com"
									target="_blank"
									rel="noopener noreferrer"
									aria-label="Abrir demo en vivo de PlaceMark"
								>
									<img src="/images/projects/placemark-logo.png" alt="" />
									<span class="project-cover-label">Lugares · Datos · Backend</span>
								</a>
								<p class="project-meta">Full-stack · MongoDB</p>
								<h3 class="title is-5">PlaceMark</h3>
								<p>
									Sistema full-stack con arquitectura backend estructurada, persistencia de datos y
									renderizado del lado del servidor.
								</p>
								<p class="project-links">
									<a
										href="https://github.com/edabelt/PlaceMark"
										target="_blank"
										rel="noopener noreferrer">GitHub</a
									>
									·
									<a
										href="https://placemark-a2vl.onrender.com"
										target="_blank"
										rel="noopener noreferrer">Demo en vivo</a
									>
								</p>
							</div>
						</article>
					</div>

					<div class="column is-half">
						<article class="card project-card">
							<div class="card-content">
								<a
									class="project-card-cover project-card-cover-compact"
									href="https://weathertop-c23k.onrender.com/stations/357a27fb-34ce-423c-a5e8-0fd22544fec3/overview"
									target="_blank"
									rel="noopener noreferrer"
									aria-label="Abrir demo en vivo de WeatherTop"
								>
									<img src="/images/projects/weathertop-logo.png" alt="" />
									<span class="project-cover-label">Estaciones · Dashboards · APIs</span>
								</a>
								<p class="project-meta">Full-stack · APIs</p>
								<h3 class="title is-5">WeatherTop</h3>
								<p>
									Sistema orientado a datos con integración de APIs RESTful, dashboards y
									visualización meteorológica en tiempo real.
								</p>
								<p class="project-links">
									<a
										href="https://github.com/edabelt/WeatherTop"
										target="_blank"
										rel="noopener noreferrer">GitHub</a
									>
									·
									<a
										href="https://weathertop-c23k.onrender.com/stations/357a27fb-34ce-423c-a5e8-0fd22544fec3/overview"
										target="_blank"
										rel="noopener noreferrer"
									>
										Demo en vivo
									</a>
								</p>
							</div>
						</article>
					</div>

					<div class="column is-half">
						<article class="card project-card">
							<div class="card-content">
								<a
									class="project-card-cover project-card-cover-compact"
									href="https://whether-weather-app.netlify.app/"
									target="_blank"
									rel="noopener noreferrer"
									aria-label="Abrir demo en vivo de Whether-Weather"
								>
									<img src="/images/projects/whether-weather-logo.png" alt="" />
									<span class="project-cover-label">Pronóstico · Interfaz · API</span>
								</a>
								<p class="project-meta">Frontend · APIs</p>
								<h3 class="title is-5">Whether-Weather</h3>
								<p>
									Interfaz web multipágina con consumo de APIs, diseño responsivo y estructura clara
									de información.
								</p>
								<p class="project-links">
									<a
										href="https://github.com/edabelt/Whether-Weather"
										target="_blank"
										rel="noopener noreferrer">GitHub</a
									>
									·
									<a
										href="https://whether-weather-app.netlify.app/"
										target="_blank"
										rel="noopener noreferrer">Demo en vivo</a
									>
								</p>
							</div>
						</article>
					</div>
				</div>
			</section>
		</div>
	</section>
</main>
