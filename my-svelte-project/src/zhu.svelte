<script>
export let list;
let arr=[]
let newArr=[]
function change(id){
    arr.push(id)
    newArr=Array.from(new Set(arr))
}
</script>
<style>
.product{
    width:100%;
    height:100%;
    display: flex;
    flex-wrap:wrap;
}
.product .every{
    width:50%;
    height:300px;
}
.product .every img{
    width:90%;
    height:60%;
}
.addProduct{
    padding:6px 3px;
    background: orange;
    color: white;
}
</style>
<div class="product">
    {#each list as item}
        <div class="every">
            <img src="{item.src}" alt="">
            <p>{item.name}</p>
            <span>{item.price}</span>
            <span class="addProduct" on:click={()=>{
               change(item.id)
               window.localStorage.setItem('product',JSON.stringify(newArr))
            }}>加入购物车</span>
        </div>
    {/each}
</div>