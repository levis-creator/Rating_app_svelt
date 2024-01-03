<script>
  import FeedBackForm from "./components/FeedBackForm.svelte";
  import FeedBackStats from "./components/FeedBackStats.svelte";
  import FeedbackList from "./components/FeedbackList.svelte";
  import { FeedBackStore } from "./data/store";
  $: count = $FeedBackStore.length;
  $: average =
    $FeedBackStore.reduce((a, { rating }) => a + rating, 0) /
    $FeedBackStore.length;
</script>

<main class="container mx-auto px-10 py-7">
  <FeedBackForm  />
  <FeedBackStats {count} {average} />
  <FeedbackList />
</main>
