<template>
    <div>
        <table id="firstTable">
            <thead>
            <tr>
                <th>nummer</th>
                <th>vraag</th>
                <th>jouw Antwoord</th>
                <th>juiste Antwoord</th>
                <th>oordeel</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="vraag in vragen" :key="vraag.vraagNummer">
                <td>{{vraag.getVraagNummer()}}</td>
                <td>{{vraag.getVraag()}}</td>
                <td>{{vraag.getGegevenAntwoordVolledig()}}</td>
                <td>{{vraag.getJuisteAntwoordVolledig()}}</td>
                <td>{{vraag.isGoed()}}</td>
            </tr>
            </tbody>
        </table>
        <button id="opnieuw" @click="opnieuw" class="navigatie">Opnieuw</button>
    </div>
</template>

<script>
    export default {
        name: "Resultaten",
        props: {
            vragen: {
                type: Array,
                required:true
            }
        },
        methods: {
            opnieuw: function () {
                this.$emit('opnieuw')
            }
        }
    }
</script>

<style scoped>
    table {
        font-family: 'Open Sans', sans-serif;
        width: 750px;
        border-collapse: collapse;
        border: 3px solid #44475C;
        margin: 10px auto;
    }

    table th {
        text-transform: uppercase;
        text-align: left;
        background: #44475C;
        color: #FFF;
        padding: 8px;
        min-width: 30px;
    }

    table td {
        text-align: left;
        padding: 8px;
        border-right: 2px solid #7D82A8;
    }
    table td:last-child {
        border-right: none;
    }
    table tbody tr:nth-child(2n) td {
        background: #D4D8F9;
    }

    .navigatie {
        display:block;
        background-color: #595959;
        color: white;
        width: 230px;
        padding: 7px;
        border-radius: 50px;
        font-size: 28px;
        font-weight: 900;
        font-family: serif;
        margin: 25px auto;
        border: 1px solid grey;
        text-align: center;
        box-shadow: 2px 2px 0px 0px rgba(191,191,191,0.5);
    }

    #opnieuw:hover
    {
        cursor: pointer;
        background-color: #808080;
    }

</style>