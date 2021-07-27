<template>
    <div className="card special" >
        <img 
            className="portrait" 
            :src="fish.portrait"
            :alt="fish.name + '\'s icon'" 
            :title="fish.name"
        />
        <h3 className="cart-tile"> {{ fish.name }} </h3>
        <span 
            className="card-special-data"
            v-for="loc in fish.location"
            :key="loc"
            v-text="loc.text"
        ></span>
    </div>
</template>

<script>
export default {
    name: "card-special",
    props: {
        fish: Object
    }
}
</script>

<style scoped>
    .card-special-data{
        padding: 1rem 0;
    }
    .special{
        align-content: center;
        grid-auto-rows: 30% 10% 20%;
        background-color: #82b1ff80;
    }
</style>