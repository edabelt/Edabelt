<script>
	const leisureActivities = [
		{
			title: 'Ajedrez',
			kicker: 'Estrategia · Patrón · Paciencia',
			image: '/images/leisure/chess.jpg',
			description:
				'El ajedrez es una práctica de atención lenta: leer posiciones, sostener varios futuros a la vez y ver cómo una pequeña jugada transforma todo el campo.'
		},
		{
			title: 'Baile',
			kicker: 'Ritmo · Cuerpo · Escucha',
			image: '/images/leisure/dancing.jpg',
			description:
				'Bailar mantiene el pensamiento encarnado. Entrena el tiempo, la relación, la improvisación y una percepción que ocurre antes de que el lenguaje la alcance.'
		},
		{
			title: 'Cocina',
			kicker: 'Comida · Juego · Hospitalidad',
			image: '/images/leisure/cooking.jpg',
			description:
				'Me encanta cocinar porque, por supuesto, soy un foodie guy: curioso por el sabor, la textura, las combinaciones raras y la alegría de convertir ingredientes en una escena compartida.'
		},
		{
			title: 'Gimnasio',
			kicker: 'Disciplina · Fuerza · Forma',
			image: '/images/leisure/gym.jpg',
			description:
				'El gimnasio es un espejo de la debilidad. No siempre logro ser consistente, y por eso mismo importa: me muestra dónde todavía debo construir disciplina.'
		},
		{
			title: 'Chess boxing',
			kicker: 'Cálculo · Presión · Control',
			image: '/images/leisure/chess-boxing.jpg',
			description:
				'El chess boxing concentra dos intensidades: calma táctica y presión física. Me interesa esa inteligencia que debe seguir lúcida bajo fatiga. Me encanta dejar de filosofar con un golpe, mate.'
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
