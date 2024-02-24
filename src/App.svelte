<script lang="ts">
	import FeedbackForm from './components/FeedbackForm.svelte'
	import FeedbackList from './components/FeedbackList.svelte'; 
	import FeedbackStats from './components/FeedbackStats.svelte'
	let feedback = [
		{
			id : 1,
			rating : 10,
			text : 'some random feedback about svelte , in the begining it sucks like it feels like shit but i have to try it and compare it with react to see the disadvantages or the advantages'
		},
		{
			id : 2,
			rating : 9,
			text : 'some random feedback about svelte , in the begining it sucks like it feels like shit but i have to try it and compare it with react to see the disadvantages or the advantages'
		},
		{
			id : 3,
			rating : 4,
			text : 'some random feedback about svelte , in the begining it sucks like it feels like shit but i have to try it and compare it with react to see the disadvantages or the advantages'
		}
	]
	$: count = feedback.length
	$: avg = feedback.reduce((acc , curr) => acc+curr?.rating,0) / count
	const deleteFeedback = (e) => {
		const itemId = e.detail
		feedback = feedback.filter((f) => f.id !== itemId)
	}
</script>

<main class="container">
	<FeedbackForm/>
	<FeedbackStats {count} average={avg} />
	<FeedbackList {feedback} on:delte-feedback={deleteFeedback}/>
</main>

