<template>
    <div  class="nos"><slot></slot></div>
</template>

<script>
    export default {
        name: "VraagNummer",
    }
</script>

<style scoped>
    .nos {
        width: 50px;
        height: 50px;
        background-color: #8c8c8c;
        border-radius: 50%;
        text-align: center;
        color: white;
        padding: 11px;
        font-weight: bolder;
        font-size: 22px;
        border: 1.5px solid lightskyblue;
    }

    .gemaakt{
        background-color: green !important;
    }
    .active{
        border:3px solid orange !important;
    }
</style>