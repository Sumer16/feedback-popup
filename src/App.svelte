<script>
    import FeedbackList from "./components/FeedbackList.svelte";
	import FeedbackStats from "./components/FeedbackStats.svelte";
	import FeedbackForm from "./components/FeedbackForm.svelte";

	let feedback = [
		{
			id: 1,
			rating: 10,
			text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
		},
		{
			id: 2,
			rating: 9,
			text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
		},
		{
			id: 3,
			rating: 8,
			text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
		},
	]

	$: count = feedback.length;
	$: average = (feedback.reduce((item, {rating}) => item + rating, 0) / feedback.length).toFixed(2);

	const deleteFeedback = (e) => {
		const itemID = e.detail // from feedback item using dispatch
		console.log(itemID)
		feedback = feedback.filter((item) => {
			return item.id != itemID
		});
	}

	const addFeedback = (e) => {
		const newFeedback = e.detail;
		feedback = [newFeedback, ...feedback];
	}
</script>

<main class="container">
	<FeedbackForm on:add-feedback={addFeedback} />
	<FeedbackStats average={average} count={count} />
	<FeedbackList feedback={feedback} on:delete-feedback={deleteFeedback} />
</main>
