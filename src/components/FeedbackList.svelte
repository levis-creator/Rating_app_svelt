<script>
  import { fade, scale } from "svelte/transition";
  import FeedbackItem from "./FeedbackItem.svelte";
  import { FeedBackStore } from "../data/store";

 let feedback=[]

</script>
{#each $FeedBackStore as feed (feed.id)}
<div in:scale out:fade={{duration:500}}>

  <FeedbackItem item={feed} on:delete_feeback/>
</div>
{/each}