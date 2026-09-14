<script>
	const highlights = [
		'Interdisciplinary research',
		'Digital narrative',
		'Computer science',
		'Visual analytics',
		'AI-mediated storytelling',
		'Digital humanities'
	];

	const education = [
		{
			degree: 'Higher Diploma in Computer Science',
			institution: 'South East Technological University, Ireland',
			date: 'Jan 2025 - Present',
			result: 'GPA: 78.6%',
			details: [
				'Programming, Web Development 1 & 2, Databases, Systems & Networks, DevOps, Full-Stack Development 1 & 2.',
				'Final project in progress: an interactive film data and cultural mapping platform built with React, Supabase, D3/ECharts, and the TMDB API.'
			]
		},
		{
			degree: 'MA Digital Arts & Humanities',
			institution: 'National University of Ireland, University College Cork',
			date: '2023 - 2025',
			result: 'First Class Honours',
			details: [
				'Dissertation: Ethics and Aesthetics of Digital Narrative.',
				'Examined how digital technologies transform literary form, computational processes, datafied knowledge, and the ethical responsibilities of the humanities.'
			]
		},
		{
			degree: 'MA Philosophy',
			institution: 'Pontifical University of Salamanca, Spain',
			date: '2017 - 2019',
			result: 'GPA: 8.59/10',
			details: [
				'Dissertation on ethics, epistemology, metaphysics, and aesthetics in Schopenhauer.',
				'Connected post-Kantian limits of knowledge with ethical thought, tragedy, and aesthetic experience.'
			]
		},
		{
			degree: 'BA (Hons) Humanities',
			institution: 'Pontifical University of Salamanca, Spain',
			date: '2013 - 2017',
			result: 'GPA: 8.85/10',
			details: ['Dissertation: Creative Writing.']
		},
		{
			degree: 'BA Philosophy',
			institution: 'Pontifical University of Salamanca, Spain',
			date: '2009 - 2013',
			result: 'GPA: 8.68/10',
			details: []
		}
	];

	const projects = [
		{
			name: 'Cinema Atlas',
			type: 'Interactive film data visualisation platform',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/Cinema-Atlas' },
				{ label: 'Live demo', href: 'https://cinemaatlas-bfepyveka-edabelt.vercel.app/' }
			],
			points: [
				'Designed a platform that moves from country-level genre trends and release patterns to thematic relationships and source evidence for individual films.',
				'Implemented linked visualisations in React, TypeScript, D3, and ECharts using TMDB data.'
			]
		},
		{
			name: 'Movies App',
			type: 'React/TypeScript single-page application',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/labMoviesApp' },
				{ label: 'Live demo', href: 'https://daddymovies.vercel.app/movies/upcoming' }
			],
			points: [
				'Built discovery flows for movies and actors with routing, pagination, filtering, reviews, favourites, and playlist management.',
				'Implemented Supabase authentication, persistence, file storage, React Query caching, Storybook documentation, and Vercel deployment.'
			]
		},
		{
			name: 'The Wandering Desk',
			type: 'Full-stack geospatial workspace management platform',
			links: [
				{ label: 'Live demo', href: 'https://thewanderingdesk.netlify.app/' },
				{ label: 'Frontend', href: 'https://github.com/edabelt/thewanderingdesk-frontend' },
				{ label: 'Backend', href: 'https://github.com/edabelt/thewanderingdesk-backend' },
				{ label: 'API', href: 'https://github.com/edabelt/thewanderingdesk-api' }
			],
			points: [
				'Built a SvelteKit platform for managing workspace collections and geographic placemarks with interactive Leaflet maps, ECharts analytics, Firebase image uploads, and live OpenWeather data.',
				'Structured the system across frontend, backend, and API repositories using a Hapi.js REST API, MongoDB, JWT authentication, and secure CRUD operations.'
			]
		},
		{
			name: 'PlaceMark',
			type: 'Full-stack web application',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/PlaceMark' },
				{ label: 'Live demo', href: 'https://placemark-a2vl.onrender.com' }
			],
			points: [
				'Developed a database-driven application with structured backend models, controllers, and routes.',
				'Implemented persistence and user interaction features with MongoDB Atlas and server-side rendering.'
			]
		},
		{
			name: 'WeatherTop-IoT',
			type: 'Event-driven IoT pipeline',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/WeatherTop-iot' },
				{ label: 'Live demo', href: 'https://weathertop-iot.onrender.com/' }
			],
			points: [
				'Designed an event-driven system using MQTT for real-time telemetry processing.',
				'Integrated a messaging pipeline with a Node.js backend for data ingestion and visualisation.'
			]
		},
		{
			name: 'WeatherTop',
			type: 'Full-stack web application',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/WeatherTop' },
				{
					label: 'Live demo',
					href: 'https://weathertop-c23k.onrender.com/stations/357a27fb-34ce-423c-a5e8-0fd22544fec3/overview'
				}
			],
			points: [
				'Built a data-driven application with RESTful API integration and dashboard views.',
				'Processed and visualised real-time weather data using external APIs.'
			]
		},
		{
			name: 'Whether-Weather',
			type: 'Static web application',
			links: [
				{ label: 'GitHub', href: 'https://github.com/edabelt/Whether-Weather' },
				{ label: 'Live demo', href: 'https://whether-weather-app.netlify.app/' }
			],
			points: ['Developed a multi-page API-consuming site with responsive UI and clean layout.']
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
					aria-label="View larger profile image"
					onclick={() => (isCvPortraitOpen = true)}
				>
					<img src="/images/ever-beltran-portrait-blurred.jpg" alt="Ever David Beltrán Pinto" />
					<span>View larger</span>
				</button>
				<p class="landing-kicker">Curriculum Vitae</p>
				<h1>Ever David Beltrán Pinto</h1>
				<p>
					Interdisciplinary researcher working across philosophy, literature, digital humanities,
					and computer science. My work examines how forms of representation - from literary
					narrative to computational media and data visualisation - shape knowledge, meaning,
					agency, and aesthetic experience.
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
						rel="noopener noreferrer">Download PDF</a
					>
				</div>
			</div>

			{#if isCvPortraitOpen}
				<div
					class="cv-portrait-lightbox"
					role="dialog"
					aria-modal="true"
					aria-label="Profile image preview"
					tabindex="-1"
					onclick={closePortraitFromBackdrop}
					onkeydown={handlePortraitKeydown}
				>
					<div class="cv-portrait-preview">
						<button type="button" onclick={() => (isCvPortraitOpen = false)}>Close</button>
						<img src="/images/ever-beltran-portrait-blurred.jpg" alt="Ever David Beltrán Pinto" />
					</div>
				</div>
			{/if}

			<div class="cv-highlight-grid" aria-label="CV highlights">
				{#each highlights as highlight (highlight)}
					<span>{highlight}</span>
				{/each}
			</div>

			<section class="cv-section">
				<h2>Research Profile</h2>
				<p>
					I am particularly interested in digital narrative, AI-mediated storytelling, user agency,
					and the ethical implications of computational systems. My background combines
					philosophical and literary analysis with postgraduate training in Digital Arts and
					Humanities and Computer Science, enabling both critical inquiry and the design and
					implementation of digital applications.
				</p>
			</section>

			<section class="cv-section">
				<h2>Education</h2>
				<div class="cv-timeline">
					{#each education as item (item.title)}
						<article class="cv-timeline-item">
							<div>
								<p class="cv-date">{item.date}</p>
								<h3>{item.degree}</h3>
								<p class="cv-institution">{item.institution}</p>
								<p class="cv-result">{item.result}</p>
							</div>
							{#if item.details.length}
								<ul>
									{#each item.details as detail (detail)}
										<li>{detail}</li>
									{/each}
								</ul>
							{/if}
						</article>
					{/each}
				</div>
			</section>

			<section class="cv-section">
				<h2>Selected Projects</h2>
				<div class="cv-project-grid">
					{#each projects as project (project.title)}
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
				<h2>Technical Skills</h2>
				<div class="cv-skill-cloud">
					{#each skills as skill (skill.title)}
						<span>{skill}</span>
					{/each}
				</div>
			</section>

			<section class="cv-section">
				<h2>Professional Experience</h2>
				<div class="cv-timeline">
					<article class="cv-timeline-item">
						<p class="cv-date">2023 - Present</p>
						<h3>Web Developer (Freelance) - Remote</h3>
						<p>
							Developed small-scale web applications and content-oriented websites with responsive,
							user-focused UI using HTML, CSS, JavaScript, and Node.js, integrating APIs for dynamic
							content.
						</p>
					</article>
					<article class="cv-timeline-item">
						<p class="cv-date">2017 - 2018</p>
						<h3>Librarian - Mariannhill Monastery, Durban, South Africa</h3>
						<p>
							Digitised and organised collections, improving content accessibility and
							discoverability. Supported users and contributed to website content and information
							resources.
						</p>
					</article>
				</div>
			</section>

			<section class="cv-section cv-two-column">
				<div>
					<h2>Languages</h2>
					<ul>
						<li>Spanish: Native</li>
						<li>English: C1+ (Certified)</li>
						<li>German: Intermediate B1 (Goethe Zertifikat)</li>
						<li>Classical Languages: reading knowledge of Greek and Latin</li>
					</ul>
				</div>
				<div>
					<h2>Volunteering</h2>
					<ul>
						<li>
							Transcribathon (Europeana) - digital heritage transcription and metadata enrichment
							(2024 - Present)
						</li>
						<li>
							Community Support Volunteer, South Africa - children and youth in underserved
							communities (2017 - 2018)
						</li>
					</ul>
				</div>
			</section>
		</div>
	</section>
</main>
