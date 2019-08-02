<script>
import {onMount} from "svelte"
    let chuan="3434"
    let arr=[]
    onMount(async function(){
        let res=await fetch("/data.json");
        let result=await res.json()
        arr=result
    })
</script>
<style>
</style>
<p>dont bibi</p>
<div><slot>插槽</slot></div>
<div>
<slot name="one">one1</slot>
<slot name="two"></slot>
</div>
<div>
    {#each arr as item}
        <p>{item.name}</p>
    {/each}
</div>
<button on:click={()=>{
    arr=[...arr,{name:"小明"}]
}}>点我</button>>

