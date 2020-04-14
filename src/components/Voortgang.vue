<template>

    <div id="voortgang">
        <VraagNummer v-for="(vraag, index) in vragen" :key="vraag.id" :vraag="vraag" :huidigePlek="huidigePlek">{{ index }}</VraagNummer>
    </div>
</template>

<script>

    import VraagNummer from "./VraagNummer";

    export default {
        props: {
            vragen: {
                type: Array,
                required: true
            },
            huidigePlek: {
                type: Number,
                required: true
            }
        },
        name: "Voortgang",
        components: {VraagNummer},
    }
</script>

<style scoped>

    #voortgang {
        display:flex;
        margin: 20px auto;
        padding: 0 20px 0 20px;
        justify-content: space-around;
    }

</style>