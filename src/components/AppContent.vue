<template>
    <div 
        v-if="filterFishCounter() > 0"
        :className="`cards-content ${changeView()}`"
    >
        <card 
            v-for="(common, i) in getFishes('common')"
            :key="i"
            :fish="common"
        />
        <card-special
            v-for="(special, i) in getFishes('special')"
            :key="i"
            :fish="special"
        />
    </div>

    <div 
        v-else
        className="no-match"
    >
        <h2> No match! :[ </h2>
        <p> Try "<span className="random-fish">{{ getRandomFishName() }}</span>" </p>
        <img 
            className="uknownImg"
            :src="MisteryPufferfish" 
            alt="Mistery Pufferfish"
            title="???"
        >
    </div>
</template>

<script>
import Card from "./Card.vue"
import CardSpecial from "./CardSpecial.vue"

import data from "../assets/fish.json"
import MisteryPufferfish from '../assets/sprites/Unknown.png'


export default {
    name: "app-content",
    props: {
        filtered: String
    },
    data(){
        return{
            MisteryPufferfish
        }
    },
    components: {
        Card,
        CardSpecial
    },
    methods:{
        filterFish(fish){

            if(this.filtered === "") return fish 

            const text = this.filtered.toLowerCase()

            return fish.filter( item => {
                return item.name.toLowerCase().indexOf(text) !== -1
            })
        },
        getFishes(tag){

            return this.filterFish(data[tag])
        },
        getAllFishes(){
            const 
                c = this.filterFish(data["common"]),
                s = this.filterFish(data["special"])
            

            var all = c.concat(s)

            return all.length
        },

        filterFishCounter(){
            
            return this.filtered === "" ? 999 : this.getAllFishes() 
        },
        changeView(){

            const AllCard = this.filterFishCounter()

            if(AllCard === 3) return "content-tree"

            if(AllCard === 2) return "content-two"

            if(AllCard <= 1) return "content-one"

            return "content" 
        },
        getRandomFishName(){
            const fishes = data.common,
            min = 1,
            r = Math.floor(Math.random() * (fishes.length - min)) + min 

            return fishes[r].name 
        }
    }
}
</script>

<style>
    /*background-color: #1de9b680; (verde) other catchables*/
    /*background-color: #ff6f0080; (naranja) Crabs*/
    .cards-content{
        width: 100%;
        height: auto;
        min-height: 75vh;
        display: grid;
        grid-template-columns: repeat(4, .75fr);
        grid-auto-rows: 275px;
        gap: 2rem;
        justify-content: center;
        align-items: center;
        margin: 1rem 0;
        padding: 0 1rem;
    }
    .category-title{
        width: 100%;
        padding-left: 1rem;
        text-align: start;
    }

    .no-match{
        width: 100%;
        max-width: 750px;
        height: 60vh;
        min-height: 50px;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: auto;
        gap: 1.5rem;
        color: #fff;
    }
    .random-fish{
        color: #c4c4c4;
        font-weight: bold;
    }
    .content-tree{
        grid-template-columns: repeat(3, 250px);
    }
    .content-two{
        grid-template-columns: repeat(2, 250px);
    }
    .content-one{
        grid-template-columns: 225px;
        grid-auto-rows: 275px;
    }

    .uknownImg{
        width: 128px;
        height: 128px;
        margin: 2rem 0;
    }

    @media screen and (max-width: 1279px) and (min-width: 800px){
        
    }
    @media screen and (max-width: 796px) and (min-width: 481px){
        .cards-content{
            grid-template-columns: repeat(3, 200px);
        }
    }
    @media screen and (max-width: 480px){
        .cards-content{
            grid-template-columns: .75fr .75fr;
            grid-auto-rows: 250px;
            gap: .5rem;
            margin: 1.5rem 0;
            padding: 0 .5rem;
        }
        .content-one{
            grid-template-columns: 225px !important;
            grid-auto-rows: 350px;
        }
        .content{
            grid-auto-rows: 300px;
        }
    }
</style>