<template>
  <div class="options">
    <button v-on:click="addDice" class="btn add-dice">Agregar un dado➕</button>
    <button v-on:click="spinDice" class="btn spin-dice">Girar dado🕹🎲</button>
    <button v-on:click="deleteDice" class="btn delete-dice">
      Eliminar un dado❌
    </button>
  </div>

  <h3>Ingresa el lado de las caras y presiona enter</h3>
  <input
    type="number"
    v-model="initialSide"
    v-on:keyup.enter="updateSide"
    placeholder="Enter a sides in number"
    class="input-options"
  />

  <div class="container">
    <div v-for="(dice, index) in dices" :key="index" class="dice">
      <div v-if="dice.current <= 6" class="point-container">
        <div
          v-if="dice.current === 6 || dice.current === 5 || dice.current === 4"
          class="point value--1"
        ></div>
        <div
          v-if="
            dice.current === 6 ||
            dice.current === 3 ||
            dice.current === 2 ||
            dice.current === 4 ||
            dice.current === 5
          "
          class="point value--2"
        ></div>
        <div v-if="dice.current === 6" class="point value--3"></div>
        <div v-if="dice.current === 6" class="point value--4"></div>
        <div
          v-if="
            dice.current === 6 ||
            dice.current === 3 ||
            dice.current === 2 ||
            dice.current === 4 ||
            dice.current === 5
          "
          class="point value--5"
        ></div>
        <div
          v-if="dice.current === 6 || dice.current === 5 || dice.current === 4"
          class="point value--6"
        ></div>
        <div
          v-if="dice.current === 1 || dice.current === 3 || dice.current === 5"
          class="point value--7"
        ></div>
      </div>

      <div v-else class="number-container">
        <div class="point--number">{{ dice.current }}</div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "dg-main",

  data() {
    return {
      initialSide: 6,
      initialDice: {
        current: 1,
        previous: 1,
        sides: 6,
      },
      dices: [],
    };
  },

  created() {
    this.dices.push(this.initialDice);
  },

  methods: {
    getNumberRandom: function (value, index) {
      value.current = Math.floor(Math.random() * this.initialDice.sides) + 1;
      while (value.previous === value.current) {
        console.log("entro al while el dado", index);
        value = {
          ...value,
          current: Math.floor(Math.random() * this.initialDice.sides) + 1,
        };
      }
      value.previous = value.current;
      return value;
    },

    spinDice: function () {
      this.dices = this.dices.map(
        (value, i) => (value = { ...this.getNumberRandom({ ...value }, i) })
      );
    },

    addDice: function () {
      if (this.dices.length < 10) {
        this.dices.push(this.initialDice);
      } else {
        alert("Solo puedes agregar un maximo de 10 dados");
      }
      return this.dices;
    },

    updateSide: function () {
      this.initialDice.sides = this.initialSide;
      if(this.initialDice.sides > 20) {
          alert('El numero maximo de caras es 20');
      }
      return this.initialDice.sides;
    },

    deleteDice: function () {
      if (this.dices.length === 1) {
        alert(`No puedes eliminar todos los dados`);
      } else {
        this.dices.pop(this.initialDice);
      }
    },
  },
};
</script>

<style scoped>
header {
  height: 100px;
  width: 100vw;
}

.nav__img {
  height: 70px;
  width: 70px;
}

.options {
  display: flex;
  flex-direction: row;
  justify-content: center;
  height: 80px;
  margin-top: 10px;
  width: 100vw;
}

.btn {
  background-color: rgb(214, 89, 114);
  border-radius: 20px;
  font-size: 1.2rem;
  margin: 0 auto;
  width: 170px;
  height: 60px;
  margin: 10px;
}

.input-options {
  font-size: 1.5rem;
  outline: none;
  height: 30px;
}

.container {
  padding-top: 15px;
  width: 100vw;
  height: 500px;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  flex-wrap: wrap;
  margin: 20px;
}

.dice {
  position: relative;
  background: #fff;
  border: 5px solid rgb(107, 100, 100);
  border-radius: 20px;
  box-shadow: 0 70px 40px -20px rgba(0, 0, 0, 0.2);
  height: 200px;
  transform: perspective(750px) translate3d(0, 0, -100px) rotateX(15deg)
    scale(0.9, 0.9);
  transition: 0.5s ease-in-out transform;
  width: 200px;
}

.point__container {
  width: 200px;
  height: 200px;
}

.point {
  border-radius: 100%;
  position: absolute;
  width: 40px;
  height: 40px;
}

.value--1 {
  background-color: rosybrown;
  left: 10px;
  top: 10px;
}

.value--2 {
  background-color: aqua;
  right: 10px;
  top: 10px;
}

.value--3 {
  background-color: chocolate;
  left: 10px;
  top: 50%;
  transform: translate(0, -50%);
}

.value--4 {
  background-color: cadetblue;
  right: 10px;
  top: 50%;
  transform: translate(0, -50%);
}

.value--5 {
  background-color: coral;
  left: 10px;
  bottom: 10px;
}

.value--6 {
  background-color: cornflowerblue;
  right: 10px;
  bottom: 10px;
}

.value--7 {
  background-color: yellowgreen;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
.number__container {
  width: 200px;
  height: 200px;
}

.point--number {
  font-size: 6rem;
  position: absolute;
  height: 100px;
  width: 100px;
  transform: translate(60%, 50%);
}
</style>