<script>
  import { createEventDispatcher } from "svelte";

  export let value;
  let selected = 10;
  const dispatch = createEventDispatcher();
  const onChange = (e) => {
    let select = e.currentTarget.value;
    dispatch("ratingSelect", select);
    console.log(select)
  };
</script>

<div
  class=" relative w-[50px] h-[50px] p-[10px] text-center rounded-full text-lg border hover:bg-pink-500 hover:text-white"
>
  <input
    class="checked:bg-pink-500 checked:text-white ring-offset-0 outline-0"
    type="radio"
    name="rating"
    id={`num${value}`}
    {value}
    on:change={onChange}
    checked={selected === value}
  />
  <label
    class="absolute top-0 right-0 left-0 bottom-0 p-[10px] rounded-full"
    for={`num${value}`}>{value}</label
  >
</div>
