<script>
	const leisureActivities = [
		{
			title: 'Chess',
			kicker: 'Strategy · Pattern · Patience',
			image: '/images/leisure/chess.jpg',
			description:
				'Chess is where I practise slow attention: reading positions, holding several futures in mind, and learning how a small move changes the whole field.'
		},
		{
			title: 'Dancing',
			kicker: 'Rhythm · Body · Listening',
			image: '/images/leisure/dancing.jpg',
			description:
				'Dancing keeps thinking embodied. It trains timing, relation, improvisation, and the kind of perception that happens before language catches up.'
		},
		{
			title: 'Cooking',
			kicker: 'Food · Play · Hospitality',
			image: '/images/leisure/cooking.jpg',
			description:
				'I love cooking because, of course, I am a foodie guy: curious about flavour, texture, odd pairings, and the small joy of turning ingredients into a shared scene.'
		},
		{
			title: 'Gym',
			kicker: 'Discipline · Strength · Form',
			image: '/images/leisure/gym.jpg',
			description:
				'Gym is a mirror of weakness. I cannot always be consistent with it, but that is exactly why it matters: it shows me where discipline still has to be built.'
		},
		{
			title: 'Chess boxing',
			kicker: 'Calculation · Pressure · Control',
			image: '/images/leisure/chess-boxing.jpg',
			description:
				'Chess boxing condenses two kinds of intensity: tactical calm and physical pressure. I like the idea of intelligence that must stay lucid under fatigue. I love to stop philosophising with a punch, mate.'
		}
	];
</script>

<main>
	<section class="section">
		<div class="container is-max-desktop leisure-page">
			<p class="is-size-7 has-text-grey mb-3">Leisure activities</p>
			<h1 class="title is-2 mb-5">Leisure as another kind of training.</h1>

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
