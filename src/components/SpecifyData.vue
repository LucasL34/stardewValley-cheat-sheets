<template>
    <div className="specify-container">
        <span>
            <b>{{ fishName }}</b> ▸ details 
        </span>
        
        <section    
            v-if="specifyData.location !== undefined"
            className="specify-section"
        >
            <img
                src="https://34sprites-stardew.000webhostapp.com/stardew-icons/World.png" 
                className="icon"
            />
            <div className="specify-item">
                <div 
                    v-for="(loc, i) in specifyData.location"
                    :key="i"
                    className="specify-item"
                >
                    <b> {{loc.origin}} </b>
                    <i> {{loc.specify}} </i>
                </div>
            </div>
        </section>

        <section
            v-if="specifyData.season !== undefined"
            className="specify-section"
        >
            <img 
                src="https://34sprites-stardew.000webhostapp.com/stardew-icons/Search.png"
                className="icon"
            />
            <div className="specify-item">
                <div
                    v-for="(season, i) in specifyData.season"
                    :key="i"
                    className="specify-item"
                >
                    <b> {{season.origin}} </b>
                    <i> {{season.specify}} </i>
                </div>
            </div>
        </section>

    </div>
</template>

<script>
export default {
    name: "specify-data",
    props: {
        specifyData: Object,
        fishName: String
    }
}
</script>

<style scoped>
    .specify-container{
        position: absolute;
        width: 100%;
        height: 100%;
        background-color: #c4c4c4;
        color: #171717;
        border-radius: 8px;
        padding: 3rem .5rem .5rem;
        overflow: auto;
    }
    .specify-section{
        display: flex;
        text-align: start;
        margin: 1rem 0;
    }
    .specify-item{
        width: 90%;
        display: flex;
        flex-direction: column;
        margin-left: 1rem;
    }
    .icon{
        width: 24px;
        height: 24px;
        margin: auto;
    }
</style>