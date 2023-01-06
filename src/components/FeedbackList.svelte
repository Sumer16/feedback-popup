<script>
    import { FeedbackStore } from "../stores";
    
    import { fade, scale } from "svelte/transition";

    import FeedbackItem from "./FeedbackItem.svelte";
</script>

{#each $FeedbackStore as feed (feed.id)}
    <div in:scale out:fade="{{ duration: 400 }}">
        <FeedbackItem item={feed} />
    </div>
{/each}