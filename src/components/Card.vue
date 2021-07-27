<template>
    <div :className="`card ${fish.type}`" >
        <div v-if="fish.hasSpecified !== null" className="help-bar">
            <input 
                v-show="false" 
                type="checkbox" 
                :id="dataSpecifyId" 
                @change="ToggleSpecifyContainer"
            />
            <label
                :for="dataSpecifyId"
                :className="'specify-btn ' + [ dataSpecifyState ? 'btn-on' : '']"
                v-text="'...'"
            />
        </div>
        <specify-data 
            v-if="dataSpecifyState === true" 
            :specifyData="fish.hasSpecified" 
            :fishName="fish.name"
        />

        <img 
            className="portrait" 
            :src="fish.portrait"
            :alt="fish.name + '\'s icon'" 
            :title="fish.name"
        />
        <h3 className="cart-tile"> {{ fish.name }} </h3>
        <table-data :item="fish" />
    </div>
</template>

<script>
import TableData from "./TableData.vue"
import SpecifyData from "./SpecifyData.vue"

export default {
    name: "Card",
    props: {
        fish: Object
    },
    data(){
        return{      
            dataSpecifyState: false,
            dataSpecifyId: `specify-data-${this.fish.id}`
        }
    },
    components: {
        TableData,
        SpecifyData
    }, 
    methods: {
        ToggleSpecifyContainer(){
            this.dataSpecifyState = !this.dataSpecifyState
        }
    }
}
</script>

<style>
    .card{
        width: 100%;
        max-width: 225px;
        height: 100%;
        position: relative;
        display: grid;
        grid-auto-rows: 25% 10% 60%;
        grid-template-columns: 1fr;
        border-radius: 8px;
        align-content: end;
        margin: 0 auto;
        color: #fff;
        user-select: none;
    }

    .help-bar{
        width: 100%;
        height: 30px;
        position: absolute;
        top: 0;
        text-align: end;
        padding-right: 1rem;
        z-index: 3;
    }
    .specify-btn{
        font-size: 1.75rem;
        font-weight: bold;
        cursor: pointer;
    }
    .btn-on{
        color: #171717;
    }

    .common{
        background-color: #0277bd80;
    }
    .legendary{
        background-color: #7b1fa280;
    }

    .portrait{
        margin: auto;
    }
</style>