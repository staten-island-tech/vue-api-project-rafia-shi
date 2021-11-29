<template>
<div>fatin </div>
  
</template>

<script>
export default {
name: "GamePreview",
props: ["game", "id", ],
data(){
    return{
        singleGame:{}
    }
},
mounted: function(){
    this.fetchData2();
    console.log(this.singleGame)

},
methods:{
    fetchData2: async function (){
        try {
            const result = await fetch(`https://www.cheapshark.com/api/1.0/deals?storeID=1&upperPrice=15`);
            const singleGame = await result.json();
            this.singleGame = singleGame;
            
        } catch (error) {
            console.log(error);
        }
    }

}
};

</script>

<style>

</style> 