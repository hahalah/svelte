<script>
    export let list;
    let brr=[];
    let sum=0;
    let num=0;
 let aa=JSON.parse(localStorage.getItem("product"))
    list.forEach((item,i)=>{
        aa.forEach((val,i)=>{
            if(item.id===val){
                item.num=1
                brr.push(item)
                console.log(brr)
            }
        })
    })
    function sumPrice(){
        sum=brr&&brr.reduce((per,cur)=>{
            return per+cur.num*cur.price
        },0)
        console.log(sum)
        num=brr&&brr.reduce((per,cur)=>{
            return per+cur.num
        },0)
        console.log(num)
    }
    sumPrice()
   function jian(ind){
       brr.forEach((item,i)=>{
       if(item.id===ind){
           if(item.num>1){
               item.num=item.num-1;
           }
           else if(item.num<1){
               item.num=1;
           }
       }
    })
    brr=brr
     sumPrice()
   }
   function add(ind){
       brr.forEach((item,i)=>{
       if(item.id===ind){
           item.num=item.num+1
       }
    })
    brr=brr
     sumPrice()
   }
</script>
<style>
.shopCar{
    width:100%;
    height:100%;
    display: flex;
    flex-direction: column;
}
.shopCar .content{
    flex:1;
}
.shopCar .sum{
    width:100%;
    height:40px;
}
.shopCar .each{ 
    width:100%;
    height:100px;
    padding:10px;
    display: flex;
}
.shopCar .each .left{
    flex:3;
}
.shopCar .each .left img{
    width:100%;
    height:100%;
}
.shopCar .each .right{
    flex:7;
}
.sum{display:flex ;
line-height: 40px;}
.sum .left{
    flex:4;
}
.sum .middle{
    flex:3;
}
.sum .right{
    flex:3;
    background: red;
    color: white;
    line-height: 40px;
    text-align: center;
}
.opera .jian,.opera .add{
    font-size:30px;
}
</style>
<div class="shopCar">
    <div class="content">
        {#each brr as item}
            <div class="each">
                <div class="left"><img src="{item.src}" alt=""></div>
                <div class="right">
                    <p>{item.name}</p>
                    <p>${item.price}</p>
                    <div class="opera">
                        <span class="jian" on:click={()=>{
                            jian(item.id)
                        }}>-</span>
                        <span>{item.num}</span>
                        <span class="add" on:click={()=>{
                            add(item.id)
                        }}>+</span>
                    </div>
                </div>
            </div>
        {/each}
    </div>
    <div class="sum">
        <div class="left">
        <span>全选</span>
        </div>
        <div class="middle">
        <span>总计:</span>
        <span>￥{sum}</span>
        </div>
        <div class="right">去结算<span>{num}</span>件</div>
    </div>
</div>
