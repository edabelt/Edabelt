<script>
	const highlights = [
		'Investigación interdisciplinaria',
		'Narrativa digital',
		'Ciencias de la computación',
		'Analítica visual',
		'IA y narración',
		'Humanidades digitales'
	];

	const education = [
		{
			degree: 'Higher Diploma in Computer Science',
			institution: 'South East Technological University, Irlanda',
			date: 'Ene 2025 - Actualidad',
			result: 'GPA: 78.6%',
			details: [
				{
					label: 'Módulos seleccionados:',
					text: 'Programación, Desarrollo Web 1 y 2, Bases de Datos, Sistemas y Redes, DevOps, Full-Stack Development 1 y 2.'
				},
				{
					text: 'Proyecto final en curso: plataforma interactiva de datos cinematográficos y cartografía cultural con React, Supabase, D3/ECharts y TMDB API.'
				}
			]
		},
		{
			degree: 'Máster en Digital Arts & Humanities',
			institution: 'National University of Ireland, University College Cork',
			date: '2023 - 2025',
			result: 'First Class Honours',
			details: [
				{ label: 'Disertación:', text: 'Ética y estética de la narrativa digital.' },
				{
					text: 'Analiza cómo las tecnologías digitales transforman la forma literaria, los procesos computacionales, la datificación del conocimiento y las responsabilidades éticas de las humanidades.'
				}
			]
		},
		{
			degree: 'Máster en Filosofía',
			institution: 'Pontificia Universidad de Salamanca, España',
			date: '2017 - 2019',
			result: 'Nota media: 8.59/10',
			details: [
				{
					label: 'Disertación:',
					text: 'ética, epistemología, metafísica y estética en Schopenhauer.'
				},
				{
					text: 'Conecta los límites postkantianos del conocimiento con pensamiento ético, tragedia y experiencia estética.'
				}
			]
		},
		{
			degree: 'Grado en Humanidades',
			institution: 'Pontificia Universidad de Salamanca, España',
			date: '2013 - 2017',
			result: 'Nota media: 8.85/10',
			details: [{ label: 'Disertación:', text: 'Escritura creativa.' }]
		},
		{
			degree: 'Grado en Filosofía',
			institution: 'Pontificia Universidad de Salamanca, España',
			date: '2009 - 2013',
			result: 'Nota media: 8.68/10',
			details: []
		}
	];

	const projects = [
		{
			name: 'Cinema Atlas',
			type: 'Plataforma interactiva de visualización de datos cinematográficos',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/Cinema-Atlas' },
				{ label: 'Demo', href: 'https://cinemaatlas-bfepyveka-edabelt.vercel.app/' }
			],
			points: [
				'Diseñé una plataforma que va desde tendencias de género por país y patrones temporales de estreno hasta relaciones temáticas y evidencia de películas individuales.',
				'Implementé visualizaciones conectadas en React, TypeScript, D3 y ECharts usando datos de TMDB.'
			]
		},
		{
			name: 'Movies App',
			type: 'Aplicación single-page en React/TypeScript',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/labMoviesApp' },
				{ label: 'Demo', href: 'https://daddymovies.vercel.app/movies/upcoming' }
			],
			points: [
				'Construí flujos de descubrimiento para películas y actores con rutas, paginación, filtros, reseñas, favoritos y playlists.',
				'Implementé autenticación, persistencia y almacenamiento con Supabase, cache con React Query, documentación en Storybook y despliegue en Vercel.'
			]
		},
		{
			name: 'The Wandering Desk',
			type: 'Plataforma full-stack geoespacial para gestión de espacios de trabajo',
			links: [
				{ label: 'Demo', href: 'https://thewanderingdesk.netlify.app/' },
				{ label: 'Frontend', href: 'https://github.com/edabelt/thewanderingdesk-frontend' },
				{ label: 'Backend', href: 'https://github.com/edabelt/thewanderingdesk-backend' },
				{ label: 'API', href: 'https://github.com/edabelt/thewanderingdesk-api' }
			],
			points: [
				'Construí una plataforma en SvelteKit para gestionar colecciones de espacios de trabajo y placemarks geográficos con mapas interactivos en Leaflet, analítica con ECharts, subida de imágenes a Firebase y datos en vivo de OpenWeather.',
				'Estructuré el sistema en repositorios de frontend, backend y API usando una API REST con Hapi.js, MongoDB, autenticación JWT y operaciones CRUD seguras.'
			]
		},
		{
			name: 'PlaceMark',
			type: 'Aplicación web full-stack',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/PlaceMark' },
				{ label: 'Demo', href: 'https://placemark-a2vl.onrender.com' }
			],
			points: [
				'Desarrollé una aplicación orientada a base de datos con modelos, controladores y rutas estructuradas.',
				'Implementé persistencia e interacción de usuarios con MongoDB Atlas y renderizado del lado del servidor.'
			]
		},
		{
			name: 'WeatherTop-IoT',
			type: 'Pipeline IoT orientado a eventos',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/WeatherTop-iot' },
				{ label: 'Demo', href: 'https://weathertop-iot.onrender.com/' }
			],
			points: [
				'Diseñé un sistema orientado a eventos con MQTT para procesar telemetría en tiempo real.',
				'Integré un pipeline de mensajería con backend en Node.js para ingesta y visualización de datos.'
			]
		},
		{
			name: 'WeatherTop',
			type: 'Aplicación web full-stack',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/WeatherTop' },
				{
					label: 'Demo',
					href: 'https://weathertop-c23k.onrender.com/stations/357a27fb-34ce-423c-a5e8-0fd22544fec3/overview'
				}
			],
			points: [
				'Construí una aplicación orientada a datos con integración de APIs RESTful y vistas de dashboard.',
				'Procesé y visualicé datos meteorológicos en tiempo real usando APIs externas.'
			]
		},
		{
			name: 'Whether-Weather',
			type: 'Aplicación web estática',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/Whether-Weather' },
				{ label: 'Demo', href: 'https://whether-weather-app.netlify.app/' }
			],
			points: ['Desarrollé un sitio multipágina con consumo de APIs, UI responsiva y layout claro.']
		}
	];

	const skills = [
		'React',
		'TypeScript',
		'SvelteKit',
		'Node.js',
		'Express',
		'Hapi',
		'MongoDB',
		'Mongoose',
		'Supabase',
		'Python',
		'D3',
		'ECharts',
		'MQTT',
		'AWS',
		'HTML',
		'CSS',
		'JavaScript'
	];

	let isCvPortraitOpen = $state(false);

	function handlePortraitKeydown(event) {
		if (event.key === 'Escape') {
			isCvPortraitOpen = false;
		}
	}

	function closePortraitFromBackdrop(event) {
		if (event.target === event.currentTarget) {
			isCvPortraitOpen = false;
		}
	}
</script>

<svelte:window onkeydown={handlePortraitKeydown} />

<main>
	<section class="section cv-hero-section">
		<div class="container is-max-desktop cv-page cv-page-rich">
			<div class="cv-hero">
				<button
					type="button"
					class="cv-profile-trigger"
					aria-label="Ver imagen de perfil más grande"
					onclick={() => (isCvPortraitOpen = true)}
				>
					<img src="/images/ever-beltran-portrait-blurred.jpg" alt="Ever David Beltrán Pinto" />
					<span>Ver más grande</span>
				</button>
				<p class="landing-kicker">Curriculum Vitae</p>
				<h1>Ever David Beltrán Pinto</h1>
				<p>
					Investigador interdisciplinario entre filosofía, literatura, humanidades digitales y
					ciencias de la computación. Mi trabajo examina cómo las formas de representación - desde
					la narrativa literaria hasta los medios computacionales y la visualización de datos -
					configuran conocimiento, sentido, agencia y experiencia estética.
				</p>
				<div class="cv-contact-row">
					<a href="https://edabelt.netlify.app" target="_blank" rel="noopener noreferrer"
						>Portfolio</a
					>
					<a href="mailto:edbeltranpi.chs@gmail.com">Email</a>
					<a href="https://github.com/edabelt" target="_blank" rel="noopener noreferrer">GitHub</a>
					<a
						class="button is-light"
						href="/files/Ever_David_Beltran_CV.pdf"
						target="_blank"
						rel="noopener noreferrer">Descargar PDF</a
					>
				</div>
			</div>

			{#if isCvPortraitOpen}
				<div
					class="cv-portrait-lightbox"
					role="dialog"
					aria-modal="true"
					aria-label="Vista ampliada de la imagen de perfil"
					tabindex="-1"
					onclick={closePortraitFromBackdrop}
					onkeydown={handlePortraitKeydown}
				>
					<div class="cv-portrait-preview">
						<button type="button" onclick={() => (isCvPortraitOpen = false)}>Cerrar</button>
						<img src="/images/ever-beltran-portrait-blurred.jpg" alt="Ever David Beltrán Pinto" />
					</div>
				</div>
			{/if}

			<div class="cv-highlight-grid" aria-label="Aspectos destacados del CV">
				{#each highlights as highlight (highlight)}
					<span>{highlight}</span>
				{/each}
			</div>

			<section class="cv-section">
				<h2>Perfil de Investigación</h2>
				<p>
					Me interesan especialmente la narrativa digital, la narración mediada por IA, la agencia
					del usuario y las implicaciones éticas de los sistemas computacionales. Mi formación
					combina análisis filosófico y literario con estudios de posgrado en Digital Arts and
					Humanities y Computer Science, lo que permite unir investigación crítica con diseño e
					implementación de aplicaciones digitales.
				</p>
			</section>

			<section class="cv-section cv-education-section">
				<h2>Formación Académica</h2>
				<div class="cv-timeline cv-education-list">
					{#each education as item (item.degree)}
						<article class="cv-timeline-item">
							<div>
								<p class="cv-date">{item.date}</p>
								<h3>{item.degree}</h3>
								<p class="cv-institution">{item.institution}</p>
								<p class="cv-result">{item.result}</p>
							</div>
							{#if item.details.length}
								<ul>
									{#each item.details as detail (detail.text)}
										<li>
											{#if detail.label}
												<strong>{detail.label}</strong>
											{/if}
											{detail.text}
										</li>
									{/each}
								</ul>
							{/if}
						</article>
					{/each}
				</div>
			</section>

			<section class="cv-section">
				<h2>Proyectos Seleccionados</h2>
				<div class="cv-project-grid">
					{#each projects as project (project.name)}
						<article class="cv-project-card">
							<p class="project-type">{project.type}</p>
							<h3>{project.name}</h3>
							<ul>
								{#each project.points as point (point)}
									<li>{point}</li>
								{/each}
							</ul>
							<div class="project-link-row">
								{#each project.links as link (link.href)}
									<a href={link.href} target="_blank" rel="noopener noreferrer">{link.label}</a>
								{/each}
							</div>
						</article>
					{/each}
				</div>
			</section>

			<section class="cv-section">
				<h2>Habilidades Técnicas</h2>
				<div class="cv-skill-cloud">
					{#each skills as skill (skill)}
						<span>{skill}</span>
					{/each}
				</div>
			</section>

			<section class="cv-section">
				<h2>Experiencia Profesional</h2>
				<div class="cv-timeline">
					<article class="cv-timeline-item">
						<p class="cv-date">2023 - Actualidad</p>
						<h3>Desarrollador Web Freelance - Remoto</h3>
						<p>
							Desarrollé aplicaciones web y sitios de pequeña escala con UI responsiva y centrada en
							el usuario usando HTML, CSS, JavaScript y Node.js, con integración de APIs para
							contenido dinámico.
						</p>
					</article>
					<article class="cv-timeline-item">
						<p class="cv-date">2017 - 2018</p>
						<h3>Bibliotecario - Monasterio de Mariannhill, Durban, Sudáfrica</h3>
						<p>
							Digitalicé y organicé colecciones, mejorando la accesibilidad y la capacidad de
							descubrimiento del contenido. Apoyé a usuarios y contribuí a recursos informativos y
							contenido web.
						</p>
					</article>
				</div>
			</section>

			<section class="cv-section cv-two-column">
				<div>
					<h2>Idiomas</h2>
					<ul>
						<li>Español: nativo</li>
						<li>Inglés: C1+ certificado</li>
						<li>Alemán: intermedio B1 (Goethe Zertifikat)</li>
						<li>Lenguas clásicas: lectura de griego y latín</li>
					</ul>
				</div>
				<div>
					<h2>Voluntariado</h2>
					<ul>
						<li>
							Transcribathon (Europeana) - transcripción de patrimonio digital y enriquecimiento de
							metadatos (2024 - Actualidad)
						</li>
						<li>
							Voluntario de apoyo comunitario, Sudáfrica - niños y jóvenes en comunidades
							desfavorecidas (2017 - 2018)
						</li>
					</ul>
				</div>
			</section>
		</div>
	</section>
</main>
