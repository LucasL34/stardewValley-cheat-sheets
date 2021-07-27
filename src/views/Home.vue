
<template>
    <input
        type="text"
        id="find-input"
        placeholder="Ej: Pufferfish"
        autocomplete="off"
        v-model="filter"
    />
    <app-content :filtered="filter" />
</template>

<script>
import AppContent from "../components/AppContent.vue"

export default {
    name: "Home",
    data(){
        return{
            filter: "",
        }
    },
    components: {
        AppContent
    }
}
</script>

<style scoped>
    #find-input{
        width: 100%;
        max-width: 500px;
        height: 5vh;
        min-height: 40px;
        border: 2px solid #171717;
        background-color: #80d2ff80;
        border-radius: 6px;
        padding: .25rem .75rem;
        margin: 3rem auto 1rem;
    }
    #find-input::placeholder{
        color: #171717;
    }

    @media screen and (max-width: 480px){
        #find-input{
            width: 75%;
            height: 6vh;
        }
    }
</style>