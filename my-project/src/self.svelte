<script>
    let arr=[
        {
        "id":0,
        "name":"猪"
        },
        {
            "id":1,
            "name":"鱼"
        }
    ]
</script>
<style>
</style>
<div>
{#each arr as item}
    <p>
    <slot item={item}></slot>
    </p>
{/each}
</div>