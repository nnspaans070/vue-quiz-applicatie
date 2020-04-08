<template>

    <div id="voortgang">
        <VraagNummer>1</VraagNummer>
        <VraagNummer>2</VraagNummer>
        <VraagNummer>3</VraagNummer>
        <VraagNummer>4</VraagNummer>
        <VraagNummer>5</VraagNummer>
        <VraagNummer>6</VraagNummer>
        <VraagNummer>7</VraagNummer>
        <VraagNummer>8</VraagNummer>
        <VraagNummer>9</VraagNummer>
        <VraagNummer>10</VraagNummer>
    </div>


</template>

<script>

    import VraagNummer from "./VraagNummer";

    export default {
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