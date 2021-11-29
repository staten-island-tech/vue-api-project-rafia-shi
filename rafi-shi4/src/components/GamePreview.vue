<template>
<div>
    <div id = "query">
        {{game.title}}
        <img :src="sprite" alt=""></div> 

        </div>
  
</template>

<script>
export default {
name: "GamePreview",
props: ["game" ],
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
            const result = await fetch(`https://www.cheapshark.com/api/1.0/deals?storeID=1&upperPrice=15${this.game.title}`);
            const singleGame = await result.json();
            this.singleGame = singleGame;
            
        } catch (error) {
            console.log(error);
        }
    }

},
 computed:{
    sprite: function(){
      return this.singleGame.thumb;
    }
  }
};

</script>

<style>
.query{
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
}

</style> 