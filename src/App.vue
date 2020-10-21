<template>
<div id="app" class="pernlung">
    <div class="lyn">
        <div class="row">
            <div class="col-md-4 col-sm-4">
                <h1>{{heron1}}</h1>
                <b-progress :value="heroh1" :max="max" show-progress animated></b-progress>
                <div class="herotitle tile">
                    <img :src="heroi1" alt class="img-fluid image" :width="heroh1 + 'vw'" />
                </div>
            </div>
            <div class="col-md-4 mt-5 col-sm-4 vs">
                <img src="./assets/vs.png" />
            </div>
            <div class="col-md-4 col-sm-4">
                <h1>{{monn1}}</h1>
                <b-progress :value="monh1" :max="max2" show-progress animated></b-progress>
                <div class="montitle tile">
                    <img :src="moni1" alt class="img-fluid image" :width="monh1 + 'vw'" />
                </div>
            </div>
        </div>
    </div>

    <div class="row">
        <div class="col-md-12 col-sm-12">
            <Game @hero_n="hero_n1" @hero_h="hero_h1" @hero_i="hero_i1" @mon_n="mon_n1" @mon_h="mon_h1" @mon_i="mon_i1" @atkp="atk_p1" @atkm="atk_m1" @spep="spe_p1" @spem="spe_m1"></Game>
        </div>
    </div>
</div>
</template>

<script>
import Game from "./components/Game";
export default {
    name: "App",
    components: {
        Game,
    },
    data: function () {
        return {
            heron1: "",
            heroh1: 0,
            heroi1: "",
            monn1: "",
            monh1: 0,
            moni1: "",
            attack: 0,
        };
    },

    methods: {
        //hero
        hero_n1(value) {
            this.heron1 = value;
        },
        hero_h1(value) {
            this.heroh1 = value;
            this.max = this.heroh1;
        },
        hero_i1(value) {
            this.heroi1 = value;
        },
        //monster
        mon_n1(value) {
            this.monn1 = value;
        },
        mon_h1(value) {
            this.monh1 = value;
            this.max2 = this.monh1;
        },
        mon_i1(value) {
            this.moni1 = value;
        },
        //attackhero
        atk_p1(value) {
            this.attack = value;
            this.monh1 -= this.attack;
        },
        spe_p1(value) {
            this.attack = value;
            this.monh1 -= this.attack;
        },
        //attackmon
        atk_m1(value) {
            this.attack = value;
            this.heroh1 -= this.attack;
        },
        spe_m1(value) {
            this.attack = value;
            this.heroh1 -= this.attack;
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #ffffff;
}

.pernlung {
    background-image: url("assets/0.jpg");
    background-repeat: on-repeat;
    background-size: 100x 100%;
    height: 100vh;
}

.lyn {
    margin: auto;
    width: 90%;
    height: 600px;
}

.herotile {
    float: center;
}

.montile {
    float: bottom;
}

.tile {
    display: inline-block;
    margin: 5px;
    bottom: 0;
}

.vs {
    margin: auto;
}
</style>
