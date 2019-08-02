<script>
import {onMount} from "svelte"
import Child from "./child.svelte"
import Self from "./self.svelte"
import Zi from "./zi.svelte"
import File from "./file.svelte"
export let name;
let num=10
let age=20
let fileArr=[]
onMount(async function(){
	let res=await fetch("/file.json")
	let result=await res.json()
	fileArr=result
})
</script>
<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {name}!{age}</h1>
<!-- <Child>
	<p>34567</p>
	<h1 slot="one">999999</h1>
	<h1 slot="two">fgfg</h1>
</Child>
<Self let:item={val}>
	<p>{val.name}</p>
</Self>
<Zi {num}>
</Zi> -->
{#if fileArr!=[]}
	<File {fileArr}></File>
{/if}


