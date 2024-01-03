<script>
  import { FeedBackStore } from "../data/store";
  import Card from "./Card.svelte";
  export let item
  const handleDelete=(itemId)=>{
    FeedBackStore.update((currentFeedback)=>{
      return currentFeedback.filter(item=>item.id!=itemId)
    })
  }
</script>
 <Card>
    <div class="absolute top-[-10px] left-[-10px] w-[50px] h-[50px] bg-pink-500 border border-white border-solid text-white text-center text-lg rounded-full flex items-center justify-center">
        {item.rating}
    </div>
    <button on:click={()=>handleDelete(item.id)} class="absolute top-[10px] right-5 cursor-pointer">
        x
    </button>
    <p>{item.text}</p>
 </Card>