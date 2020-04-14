<template>
  <div class="quiz">
    <Header />
    <Voortgang v-if="!toonResultaten" :vragen="mijnVragen" :huidigePlek="huidigePlek" />
    <hr />
    <Resultaten id="resultaat" v-on:opnieuw="opnieuw" :vragen="mijnVragen" v-if="toonResultaten" />
    <VraagVeld v-if="!toonResultaten" v-bind:vraag="mijnVragen[huidigePlek]" />
    <nav v-if="!toonResultaten">
    <button id="vorige" v-on:click="vorigeVraag" v-if="isVorigeActive" class="navigatie">Vorige Vraag</button>
      <button id="inleveren" v-if="isInleveren" @click="inleveren" class="navigatie">
        Inleveren
      </button>
    <button id="volgende" v-on:click="volgendeVraag" v-if="isVolgendeActive" class="navigatie">Volgende Vraag</button>
    </nav>
    <hr>
    <Footer />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
<script>
  import Header from "./components/Header";
  import Voortgang from "./components/Voortgang";
  import VraagVeld from "./components/VraagVeld";
  import Footer from "./components/Footer";
  import Vraag from "./data/Vraag";
  import vragen from "./data/vragen";
  import Resultaten from "./components/Resultaten";
  export default {
    components: {Resultaten, Footer, VraagVeld, Voortgang, Header},
    data() {
      return {
        vragen: vragen,
        mijnVragen: [],
        huidigePlek:0,
        toonResultaten:false,
      }
    },
    created() {
      let vraagNummer=1;
      this.vragen.forEach(
              vraag => this.mijnVragen.push(new Vraag(vraagNummer++, vraag))
      );
    },
    computed: {
      isInleveren: function () {
          let klaar=true;
          this.mijnVragen.forEach(
                  vraag => {if(vraag.isGemaakt()===false) {klaar=false;} });
          return klaar;
      },
      isVolgendeActive: function () {
        return this.huidigePlek < this.mijnVragen.length-1;
      },
      isVorigeActive: function () {
        return this.huidigePlek > 0;
      },
      inleveren: function () {
        // eslint-disable-next-line vue/no-side-effects-in-computed-properties
        return this.toonResultaten = true;
      }
    },
    methods: {
      volgendeVraag: function () {
        this.huidigePlek++;
      },
      vorigeVraag: function () {
        this.huidigePlek--;
      },
      opnieuw: function () {
        this.toonResultaten = false;
        this.mijnVragen = [];
        let vraagNummer = 1;
        this.vragen.forEach(
                vraag => this.mijnVragen.push(new Vraag(vraagNummer++, vraag))
        );
        this.huidigePlek = 0;
      },
    },
  }
</script>