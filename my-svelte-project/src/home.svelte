<script>
import Car from "./car.svelte"
import Zhu from "./zhu.svelte"
import {Router,Route,Link} from 'svelte-routing'
import {onMount} from 'svelte'
export let name;
let list=[]
onMount(async function(){
    let res=await fetch("/data.json")
    let result=await res.json()
    list=result
})
</script>
<style>
.box{
    width:100%;
    height:100%;
    margin:0;
    padding:0;
    display: flex;
    flex-direction: column;
}
.box .header{
    width:100%;
    height:40px;
    background: red;
}
.box .main{
    flex:1;
    overflow: scroll;
}
.box .foot{
    width:100%;
    height:40px;
    border-top:solid 1px #ccc;
    display: flex;
}
</style>
<div class="box">
    <div class="header"></div>
    <div class="main">
        <Router>
            <Route path="car" component={Car} {list}></Route>
            {#if list!=[]}
                <Route path="zhu" component={Zhu} {list}></Route>
            {/if}
	    </Router>
    </div>
    <div class="foot">
        <Router>
            <Link to="zhu">首页</Link>
            <Link to="type">分类</Link>
            <Link to="car">购物车</Link>
            <Link to="my">我的</Link>
	    </Router>
    </div>
</div>

