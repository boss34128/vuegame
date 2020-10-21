<template>
<div>
    <!--ได้ทั้งชื่อและ hp ออกมา-->
    <!--{{randomDamage(1,300)}} สุ่ม 1 - 300-->
    <button @click="$start" class="button-a" id="green">START</button>
    <button @click="$attack" class="button-a" id="red">ATTACK</button>
    <button @click="$special" class="button-a" id="yellow">SPECIAL ATTACK</button>
</div>
</template>

<script>
export default {
    data: function () {
        return {
            //เอาชื่อออกจาก object player[1].name
            //เอาชื่อออกจาก object player[random].name

            player: [{
                    name: "Sailor Moon",
                    hp: 305,
                    image: require("../assets/1.png"),
                },
                {
                    name: "Sailor Venus",
                    hp: 304,
                    image: require("../assets/2.png"),
                },
                {
                    name: "Sailor Mars",
                    hp: 303,
                    image: require("../assets/3.png"),
                },
                {
                    name: "Sailor Uranus",
                    hp: 302,
                    image: require("../assets/4.png"),
                },
                {
                    name: "Sailor Chibi Moon",
                    hp: 301,
                    image: require("../assets/5.png"),
                },
            ],
            monster: [{
                    name: "Cure Bloom",
                    hp: 300,
                    image: require("../assets/6.png"),
                },
                {
                    name: "Cure Egret",
                    hp: 299,
                    image: require("../assets/7.png"),
                },
                {
                    name: "Cure Mint",
                    hp: 298,
                    image: require("../assets/8.png"),
                },
                {
                    name: "Cure Pine",
                    hp: 297,
                    image: require("../assets/9.png"),
                },
                {
                    name: "Cure Burry",
                    hp: 296,
                    image: require("../assets/10.png"),
                },
            ],
        };
    },

    methods: {
        randomNO: function (min, max) {
            return Math.max(Math.floor(Math.random() * max) + 1, min);
        },
        $start: function () {
            //random
            this.ranP = this.randomNO(1, 5) - 1;
            this.ranM = this.randomNO(1, 5) - 1;
            //player
            this.nPlayer = this.player[this.ranP].name;
            this.$emit("hero_n", this.nPlayer);
            console.log("emit", this.nPlayer);
            this.hPlayer = this.player[this.ranP].hp;
            this.$emit("hero_h", this.hPlayer);
            console.log("hp", this.hPlayer);
            this.iPlayer = this.player[this.ranP].image;
            this.$emit("hero_i", this.iPlayer);
            console.log("im", this.iPlayer);
            //monster
            this.nMonster = this.monster[this.ranM].name;
            console.log("emit", this.nMonster);
            this.$emit("mon_n", this.nMonster);
            this.hMonster = this.monster[this.ranM].hp;
            this.$emit("mon_h", this.hMonster);
            this.iMonster = this.monster[this.ranM].image;
            this.$emit("mon_i", this.iMonster);
        },
        $attack: function () {
            // p -> mon
            // p <- mon
            //p <=0 ===ทำไง  you lose
            //mon <==0 ทำไง you win
            //End
            this.atk = this.randomNO(3, 10);
            this.$emit("atkp", this.atk);
            console.log("Attack :", this.atk);

            this.atk = this.randomNO(3, 10);
            this.$emit("atkm", this.atk);
            console.log("Atk back", this.atk);
        },
        $special: function () {
            this.spe = this.randomNO(10, 20);
            this.$emit("spep", this.spe);
            console.log("Special Attack :", this.spe);

            this.spe = this.randomNO(10, 20);
            this.$emit("spem", this.spe);
            console.log("SPATK back", this.spe);
        },
    },
};
</script>

<style scoped>
.b {
    font-size: 50px;
}

.button-a {
    background-color: rgb(3, 42, 77);
    border: none;
    padding: 5px 5px 5px 5px;
    text-align: center;
    display: inline-block;
    margin: 4px 2px;
    font-size: 30px;
    cursor: pointer;
    border-radius: 10px;
    border: 0.5px solid white;
    width: 300px;
}

.button-a-font-dd {
    background-color: white;
    border: none;
    color: #646363;
    padding: 5px 5px 5px 5px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    margin: 4px 2px;
    cursor: pointer;
    border-radius: 10px;
    border: 0.5px solid #ffffff;
    width: 200px;
}

button:hover#green {
    color: #2bff00;
}

button:hover#red {
    color: #ff0000;
}

button:hover#yellow {
    color: #fffb00;
}
</style>
