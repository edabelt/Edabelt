<script>
	const leisureActivities = [
		{
			title: 'Chess',
			kicker: 'Strategy · Pattern · Patience',
			image: '/images/leisure/chess.jpg',
			description: 'That is where all my mind becomes a serious game field.'
		},
		{
			title: 'Dancing',
			kicker: 'Rhythm · Body · Listening',
			image: '/images/leisure/dancing.jpg',
			description: 'Unconscious expression.'
		},
		{
			title: 'Cooking',
			kicker: 'Food · Play · Hospitality',
			image: '/images/leisure/cooking.jpg',
			description: 'I am a foodie guy.'
		},
		{
			title: 'Gym',
			kicker: 'Discipline · Strength · Form',
			image: '/images/leisure/gym.jpg',
			description: 'My weakness, I cannot be consistent at it.'
		},
		{
			title: 'Chess boxing',
			kicker: 'Calculation · Pressure · Control',
			image: '/images/leisure/chess-boxing.jpg',
			description: 'I love to stop philosophising with a punch, mate.'
		}
	];
</script>

<main>
	<section class="section">
		<div class="container is-max-desktop leisure-page">
			<p class="is-size-7 has-text-grey mb-3">Leisure activities</p>
			<h1 class="title is-2 mb-5">Leisure Activities</h1>

			<p class="writing-intro">
				The activities I return to outside research and development are not separate from how I
				think. They train attention, rhythm, discipline, strategy, and the relation between body and
				analysis.
			</p>

			<div class="leisure-grid">
				{#each leisureActivities as activity}
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
