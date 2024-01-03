<script>
export let style='primary'
export let type
export let disabled=false
</script>
<button  class="rounded-lg text-white w-[100px] h-10 cursor-pointer hover:scale-95 hover:opacity-90 disabled:bg-zinc-200 disabled:text-gray-700 disabled:scale-100 disabled:opacity-100 {style}" {type} {disabled}>
    <slot><!-- optional fallback --></slot>
</button>
