<script>
export let fileArr;
</script>
<style>
ul li{
    list-style: none;
}
img{
    width:30px;
    height:30px;
}
</style>
<div>
{#each fileArr as item}
    <ul>
        {#if item.children&&item.open}
            <li on:click={()=>item.open=!item.open}><img src="{item.icon}" alt="" />{item.name}</li>
            <svelte:self fileArr={item.children}/>
        {:else}
            <li on:click={()=>item.open=!item.open}><img src="{item.icon}" alt="" />{item.name}</li>
        {/if}
    </ul>
{/each}
</div>