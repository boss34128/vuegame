<template>
  <div>
    <p3>
    {{player[randomNO(1,3)-1].name}}</p3><br>
    <!--ได้ทั้งชื่อและ hp ออกมา-->
    <!--{{randomDamage(1,300)}} สุ่ม 1 - 300-->
    <button @click="$start" class="button-a" id="yellow">START</button>
    <button @click="$attack" class="button-a" id="purple">ATTACK</button>
    <hr />
    Name:{{aPlayer.name}}
    HP:{{aPlayer.hp}}
    image:{{aPlayer.image}}
    <hr />
    Name:{{bMonster.name}}
    HP:{{bMonster.hp}}
    image:{{bMonster.image}}
  </div>
</template>


<script>
export default {
  data: function () {
    return {
      //เอาชื่อออกจาก object player[1].name
      //เอาชื่อออกจาก object player[random].name
      aPlayer: { name: "", hp: 0, image: "" },
      bMonster: { name: "", hp: 0, image: "" },
      attack: 0,
      special: 0,
      player: [
        { name: "Lyn", hp: 90, image: "a" },
        { name: "Som", hp: 150, image: "b" },
        { name: "Stamp", hp: 200, image: "c" },
      ],
      monster: [
        { name: "Opor", hp: 60, image: "x" },
        { name: "Khatar", hp: 70, image: "y" },
        { name: "Oh", hp: 55, image: "z" },
      ],
    };
  },

  methods: {
    randomNO: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    $start: function () {
      //1.random Plaryer 1-3 -->ชื่อ ค่า hp รูป ฝากไว้ใน aPlary
      this.aPlayer = this.player[this.randomNO(1, 3) - 1];
      this.bMonster = this.monster[this.randomNO(1, 3) - 1];
      //2.random Monster 1-3
    },
    $attack: function () {
        // p -> mon
        // p <- mon
        //p <=0 ===ทำไง  you lose
        //mon <==0 ทำไง you win
        //End
        this.aPlayer = this.player[this.randomNO(1, 3) - 1];
        this.bMonster = this.monster[this.randomNO(1, 3) - 1];



    },
    $special: function () {},
  },
};
</script>

<style scoped>
.b {
  font-size: 50px;
}

.button-a {
  background-color: rgb(0, 0, 0);
  border: none;
  padding: 5px 5px 5px 5px;
  text-align: center;
  display: inline-block;
  margin: 4px 2px;
  font-size: 30px;
  cursor: pointer;
  border-radius: 10px;
  border: 0.5px solid white;
  width: 200px;
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

button:hover#yellow {
  color: #2bff00;
}
button:hover#purple {
  color: #ff0000;
}
</style>