<template>
  <div class="container">

    <div class="title">
      <h1>Analog Clock With Vuejs</h1>
    </div>

    <main>
      <div class="clock">

        <div class="Horas">
          <div class="horas" ref="horas" id="horas"></div>
        </div>

        <div class="Minutos">
          <div class="minutos" ref="minutos" id="minutos"></div>
        </div>

        <div class="Segundos">
          <div class="segundos" ref="segundos" id="segundos"></div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>

import { onMounted, ref } from 'vue';


export default {

  setup() {
    const deg = 6
    const horas = ref(null)
    const minutos = ref(null)
    const segundos = ref(null)

    onMounted(() => {
      const hr = horas.value;
      const mn = minutos.value;
      const sg = segundos.value;

      setInterval(() => {
        let day = new Date();
        let hh = day.getHours() * 30;
        let mm = day.getMinutes() * deg;
        let ss = day.getSeconds() * deg;

        hr.style.transform = `rotateZ(${(hh) + (mm / 12)}deg)`;
        mn.style.transform = `rotateZ(${mm}deg)`;
        sg.style.transform = `rotateZ(${ss}deg)`;
      })

    })

    return {
      deg, horas, minutos, segundos,
    }

  }





}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

* {
  font-family: Poppins;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  background-color: #425466;
}

main {
  height: 100vh;
  width: 100vw;
  background-color: #425466;
  display: flex;
  justify-content: center;
  align-items: center;
}

.title h1 {
  font-size: 40px;
  color: #4dba87;
  text-align: center;
}

.clock {
  display: flex;
  justify-content: center;
  align-items: center;
  background-image: url(../../public/Clock\ \(2\).png);
  background-size: cover;
  border-radius: 50%;
  box-shadow:
    0 -15px 15px rgba(255, 255, 255, 0.05),
    inset 0 -15px 15px rgba(255, 255, 255, 0.05),
    0 15px 15px rgba(0, 0, 0, 0.3),
    inset 0 15px 15px rgba(0, 0, 0, 0.3);
  height: 350px;
  width: 350px;
}

.clock::before {
  content: '';
  position: absolute;
  width: 15px;
  height: 15px;
  background-color: #4dba87;
  border-radius: 50%;
  z-index: 10000;
}

.clock .Horas,
.clock .Minutos,
.clock .Segundos {
  position: absolute;
}

.horas,
.minutos,
.segundos {
  display: flex;
  justify-content: center;
  position: absolute;
  border-radius: 50%;
}

.clock .Horas,
.horas {
  width: 160px;
  height: 160px;
}

.clock .Minutos,
.minutos {
  width: 190px;
  height: 190px;
}

.clock .Segundos,
.segundos {
  width: 230px;
  height: 230px;
}

.horas::before {
  content: '';
  position: absolute;
  width: 8px;
  height: 80px;
  background: #4dba87;
  z-index: 10;
  border-radius: 6px 6px 0 0;
}

.minutos::before {
  content: '';
  position: absolute;
  width: 4px;
  height: 90px;
  background: #4dba87;
  z-index: 11;
  border-radius: 6px 6px 0 0;
}

.segundos::before {
  content: '';
  position: absolute;
  width: 2px;
  height: 150px;
  background: red;
  z-index: 12;
  border-radius: 6px 6px 0 0;
}
</style>

