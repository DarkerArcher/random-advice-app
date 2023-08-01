<template>
  <div class="container">
    <div class="advice">
      <h1 class="advice-num">
        ADVICE #{{ adviceNum }}
      </h1>

      <p class="advice-text">
        "{{ advice }}"
      </p>
      <img class="separator" src="../assets/images/pattern-divider-desktop.svg" alt="divider">
      <div class="randomizer">
        <img src="../assets/images/icon-dice.svg" alt="dice" @click="fetchAdvice()">
      </div>
    </div>
    <div class="attribution">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>.
      Coded by <a href="https://darkerarcher.netlify.app/">Ayo Otutuloro</a>.
    </div>
  </div>
</template>

<script>
export default {
  name: 'RandomAdvice',
  data() {
    return {
      adviceNum: '',
      advice: '',
    }
  },
  methods: {
    async fetchAdvice() {
      const response = await fetch('https://api.adviceslip.com/advice')
      const data = await response.json()
      this.adviceNum = data.slip.id
      this.advice = data.slip.advice
    },
  },
}
</script>


<style>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@800&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Manrope', sans-serif;
}

body {
  background: rgb(78, 93, 115);
}

.advice {
  padding: 40px;
  display: flex;
  flex-direction: column;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 10px;
  background: rgb(50, 58, 73);
}

.advice-num {
  color: rgb(82, 255, 168);
  font-size: 12px;
  font-kerning: none;
  padding: 15px 0;
}

.advice-text {
  color: rgb(206, 227, 233);
  font-size: 28px;
}

.separator {
  padding: 30px;
}

.randomizer {
  display: flex;
  justify-content: center;
  margin: auto;
  width: fit-content;
  padding: 15px;
  background-color: rgb(82, 255, 168);
  border-radius: 50%;
  cursor: pointer;
}

.randomizer img {
  width: 20px;
  height: 20px;
}

.attribution {
  position: fixed;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  font-size: 11px; 
  text-align: center;
  padding-bottom: 10px;
  color: rgb(82, 255, 168);
}

.attribution a {
  color: rgb(206, 227, 233);
}

@media (max-width: 600px) {
  .advice {
    width: 90%;
  }

  .advice-text {
    font-size: 20px;
  }
}
</style>
