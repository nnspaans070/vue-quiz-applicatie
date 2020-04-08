<template>
    <div id="content">
        <div id="vraag">{{ fullQuestion }}</div>
        <button id="btn1" v-bind:class="{selected: isJouwAntwoord(1)}" v-on:click="setJouwAntwoord(1)" class="button"><span id="option1">{{ keuzes[0] }}</span></button>
        <button id="btn2" v-bind:class="{selected: isJouwAntwoord(2)}" v-on:click="setJouwAntwoord(2)" class="button"><span id="option2">{{ keuzes[1] }}</span></button>
        <button id="btn3" v-bind:class="{selected: isJouwAntwoord(3)}" v-on:click="setJouwAntwoord(3)" class="button"><span id="option3">{{ keuzes[2] }}</span></button>
        <button id="btn4" v-bind:class="{selected: isJouwAntwoord(4)}" v-on:click="setJouwAntwoord(4)" class="button"><span id="option4">{{ keuzes[3] }}</span></button>
    </div>
</template>

<script>
    export default {
        name: "VraagVeld",
        props: {
            vraag: {
                type: Object,
                required: true
            },
        },
        computed: {
            fullQuestion: function () {
                return this.vraag.getVraagNummer()+" "+this.vraag.getVraag();
            },
            keuzes: function () {
                return this.vraag.getKeuzes();
            }
        },
        methods: {
            isJouwAntwoord: function (nr) {
                if (this.vraag.getGegevenAntwoord() === nr) {
                    return true;
                }
                else {
                    return false;
                }
            },
            setJouwAntwoord: function (nr) {
                this.vraag.setGegevenAntwoord(nr);
            }
        }
    }
</script>

<style scoped>
    .selected {
        background-color: #99ceff !important;
    }
    #content{
        margin-top: 20px;
        padding-left: 20px;
        display:grid;
        grid-template-columns: 33.3% 33.3% 33.3%;
        grid-template-rows: 80px 50px 50px;
    }
    #vraag {
        grid-row:1 ;
        grid-column: 1 / 5;
        justify-self: start;
        font-size: 35px;
        font-weight: bold;
    }
    #btn1 {
        grid-row:2;
        grid-column:1 / 3;
    }
    #btn2 {
        grid-row:2;
        grid-column:2 / 4;
    }
    #btn3 {
        grid-row:3;
        grid-column:1 / 3;
    }
    #btn4 {
        grid-row:3;
        grid-column:2 / 4;
    }
    .button {
        justify-self: center;
        background-color: #e6f3ff;
        width: 250px;
        height: auto;
        border: 1.5px solid #339cff;
        border-radius: 75px;
        margin: 10px;
    }

    .button span {
        text-align: center;
        font-size: 20px;
        padding: 10px;
        font-weight: bold;
        color: #001a33;
    }

    .button:hover {
        background-color: #99ceff;
        cursor: pointer;
    }
</style>