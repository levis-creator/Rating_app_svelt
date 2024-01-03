<script>
  import RadioButton from "./RadioButton.svelte";
</script>

<ul class="flex justify-around  ">
  {#each { length: 10 } as _, i}
    <li>
      <RadioButton on:ratingSelect value={i + 1} />
    </li>
  {/each}
</ul>
