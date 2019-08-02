<script>
    export let num;
    console.log(num)
</script>
<style>
</style>
<div>
{#if num>5}
<p>{num}</p>
<svelte:self num={num-1}/>
{/if}
</div>