<template>
    <table className="table-data">
        <tr className="tr-data">
            <td className="td-icon" title="Location">
                <img src="https://34sprites-stardew.000webhostapp.com/stardew-icons/World.png" className="td-icon-item" alt="World icon" />
            </td>
            <td className="td-data">
                <span
                    className="td-data-item"
                    v-for="(loc, i) in item.location"
                    :key="i"
                    :title="loc"
                    v-text="loc.text"
                />
            </td>
        </tr>
        <tr className="tr-data">
            <td className="td-icon" title="Season"> 
                <img src="https://34sprites-stardew.000webhostapp.com/stardew-icons/Search.png" className="td-icon-item" alt="spyglass icon" />
            </td>
            <td className="td-data td-data-season">
                <img
                    className="td-icon-item"                
                    v-for="(season, i) in item.season"
                    :key="i"
                    :src="getIcon(season.text)"
                    :alt="season"
                />
            </td>
        </tr>
        <tr className="tr-data">
            <td className="td-icon" title="Time">
                <img src="https://34sprites-stardew.000webhostapp.com/stardew-icons/TimeIcon.png" className="td-icon-item" alt="clock icon" />
            </td>
            <td className="td-data">
                <span 
                    v-for="(time, i) in item.time"
                    :key="i"
                    className="td-data-item"
                    v-text="time"
                />
            </td>
            <td className="td-icon" :title="item.weather">
                <img 
                    className="season-icon"
                    :src="getIcon(item.weather)"
                    :alt="item.weather"
                />
            </td>
        </tr>
    </table>
</template>

<script>

export default {
    name: "table-data",
    props: {
        item: Object 
    },
    methods: {
        getIcon(text){

            return `https://34sprites-stardew.000webhostapp.com/stardew-icons/${text}.png`
        }
    }
}
</script>

<style scoped>
    .table-data{
        width: 100%;
        height: 100%;
        display: grid;
        grid-auto-rows: 1fr;
        padding: 0 .5rem;
    }
    .tr-data{
        display:flex;
        justify-content: space-between;
        align-items: center;
    }
    .td-data{
        width: 90%;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
    }
    .td-data-season{
        flex-direction: row;
        align-items: center;
    }
    .td-icon-item{
        width: 24px;
        height: 24px;
    }
    .season-icon{
        width: 26px;
        height: 18px;
    }
    .weather-icon{
        width: 42px;
        height: 30px;
    }
</style>