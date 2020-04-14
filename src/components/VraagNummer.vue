<template>
    <div @click="setHuidigePlek(getHuidigePlek)" v-bind:class="{gemaakt:isGemaakt, active:isActive}" class="nos"><slot></slot></div>
</template>

<script>
    export default {
        props: {
            vraag: {
                type: Object,
                required: true
            },
            huidigePlek: {
                type: Number,
                required: true
            }
        },
        computed: {
            isGemaakt: function () {
                if (this.vraag.isGemaakt()) {
                    return true;
                }
                else {
                    return false;
                }
            },
            isActive: function () {
                if (this.huidigePlek+1 ===this.vraag.getVraagNummer())
                {
                    return true;
                }
                else {
                    return false;
                }
            }
        },
        methods: {
            setHuidigePlek(huidigePlek)
            {
                this.$parent.$parent.setHuidigePlek(huidigePlek);
            }
        },
        getHuidigePlek:function () {
            return this.vraag.getVraagNummer()-1;
        }
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

    .nos:hover
    {
        cursor: pointer;
        background-color: #55dd55;
    }

    .gemaakt{
        background-color: green !important;
    }
    .active{
        border:3px solid orange !important;
    }
</style>