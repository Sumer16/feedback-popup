<script>
    import { fade, scale } from "svelte/transition";

    import FeedbackItem from "./FeedbackItem.svelte";

    export let feedback = [];
</script>

{#each feedback as feed (feed.id)}
    <div in:scale out:fade="{{ duration: 400 }}">
        <FeedbackItem item={feed} on:delete-feedback />
    </div>
{/each}