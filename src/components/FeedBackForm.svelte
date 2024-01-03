<script>
  import { createEventDispatcher } from "svelte";
  import Button from "./Button.svelte";
  import Card from "./Card.svelte";
  import RatingSelect from "./RatingSelect.svelte";
  import { v4 as uuidv4 } from "uuid";
  import { FeedBackStore } from "../data/store";
  let btnDisabled = true;
  $: text = "";
  let min = 10;
  let rating;
  let message;

  const dispatch = createEventDispatcher();
  const handleInput = () => {
    if (text.trim().length <= min) {
      message = `Text must be atleast ${min} characters`;
    } else {
      message = null;
      btnDisabled = false;
    }
  };
  const handleSelect = (e) => (rating = e.detail);
  const handleSubmit = () => {
    if (text.trim().length > min) {
      const newFeedBack = {
        id: uuidv4(),
        text,
        rating: +rating,
      };
      FeedBackStore.update((currentData) => {
        return [newFeedBack, ...currentData];
      });
    }
  };
</script>

<Card>
  <form on:submit|preventDefault={handleSubmit}>
    <!-- ratting select -->
    <p class="block text-center font-semibold text-2xl text-wrap mx-auto px-16">
      How would you rate your services with us?
    </p>
    <RatingSelect on:ratingSelect={handleSelect} />
    <div class="border relative rounded-lg mt-5">
      <input
        on:input={handleInput}
        bind:value={text}
        class="w-full h-full py-3 px-3 rounded-lg"
        type="text"
        name=""
        placeholder="Tell us something tha keeps you coming back"
        id=""
      />
      <div class="absolute right-1 top-0 bottom-0 flex items-center">
        <Button type="submit" disabled={btnDisabled}>Send</Button>
      </div>
    </div>

    {#if message}
      <div class="text-center">
        {message}
      </div>
    {:else}
      <span></span>
    {/if}
  </form>
</Card>
