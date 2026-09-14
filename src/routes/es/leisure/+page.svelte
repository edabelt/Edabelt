<script>
	const leisureActivities = [
		{
			title: 'Ajedrez',
			kicker: 'Estrategia · Patrón · Paciencia',
			image: '/images/leisure/chess.jpg',
			description: 'That is where all my mind becomes a serious game field.'
		},
		{
			title: 'Baile',
			kicker: 'Ritmo · Cuerpo · Escucha',
			image: '/images/leisure/dancing.jpg',
			description: 'Unconscious expression.'
		},
		{
			title: 'Cocina',
			kicker: 'Comida · Juego · Hospitalidad',
			image: '/images/leisure/cooking.jpg',
			description: 'I am a foodie guy.'
		},
		{
			title: 'Gimnasio',
			kicker: 'Disciplina · Fuerza · Forma',
			image: '/images/leisure/gym.jpg',
			description: 'My weakness, I cannot be consistent at it.'
		},
		{
			title: 'Chess boxing',
			kicker: 'Cálculo · Presión · Control',
			image: '/images/leisure/chess-boxing.jpg',
			description: 'I love to stop philosophising with a punch, mate.'
		}
	];
</script>

<main>
	<section class="section">
		<div class="container is-max-desktop leisure-page">
			<p class="is-size-7 has-text-grey mb-3">Actividades de ocio</p>
			<h1 class="title is-2 mb-5">El ocio como otra forma de entrenamiento.</h1>

			<p class="writing-intro">
				Las actividades a las que vuelvo fuera de la investigación y el desarrollo no están
				separadas de mi forma de pensar. Entrenan atención, ritmo, disciplina, estrategia y la
				relación entre cuerpo y análisis.
			</p>

			<div class="leisure-grid">
				{#each leisureActivities as activity (activity.title)}
					<article class="leisure-card">
						<img src={activity.image} alt="" loading="lazy" />
						<div class="leisure-card-body">
							<p>{activity.kicker}</p>
							<h2>{activity.title}</h2>
							<span>{activity.description}</span>
						</div>
					</article>
				{/each}
			</div>
		</div>
	</section>
</main>
