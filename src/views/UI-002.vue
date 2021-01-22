<template>
  <div>
    <h2>Countdown timer</h2>
    <h1>{{ parseSeconds(countDown) }}</h1>
    <div :style="myStyle" id="wrapper"></div>
    <div class="main">
      <div class="sub-main">
        <button class="button-one" type="button" @click="rem(3600)">
          - hr
        </button>
        <button class="button-one" type="button" @click="add(3600)">
          + hr
        </button>
      </div>
      <div class="sub-main">
        <button class="button-one" type="button" @click="rem(60)">- min</button>
        <button class="button-one" type="button" @click="add(60)">+ min</button>
      </div>
      <div class="sub-main">
        <button class="button-one" type="button" @click="rem(1)">- s</button>
        <button class="button-one" type="button" @click="add(1)">+ s</button>
      </div>
    </div>
    <div class="sub-main2">
      <button class="button-one" type="button" @click="setRunning(true)">
        Start
      </button>
      <button class="button-one" type="button" @click="setRunning(false)">
        Stop
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      countDown: 60,
      running: false,
      myStyle: {
        backgroundColor: "#16a085",
      },
    };
  },
  methods: {
    setRunning(bool) {
      this.running = bool;
    },
    parseSeconds(seconds) {
      return new Date(seconds * 1000).toISOString().substr(11, 8);
    },
    countDownTimer() {
      if (this.countDown > 0 && this.running) {
        setTimeout(() => {
          this.countDown -= 1;
          this.countDownTimer();
        }, 1000);
      }
    },
    add(sec) {
      this.countDown += parseInt(sec);
    },
    rem(sec) {
      if (this.countDown >= parseInt(sec)) {
        this.countDown -= parseInt(sec);
      }
    },
  },
  watch: {
    running: function () {
      this.countDownTimer();
    },
  },
  created() {},
};
</script>

<style scoped>
@import url(https://fonts.googleapis.com/css?family=Open+Sans:400,400italic,600,600italic,700italic);

* {
  margin: 0px;
  padding: 0px;
}

body {
  background: #2c3e50;
  font-family: "Open Sans", sans-serif;
}
h1 {
  text-align: center;
  padding: 20px;
}
button {
  color: #fff;
  text-align: center;
  padding: 20px;
}

p {
  color: #fff;
  text-align: center;
  padding-top: 500px;
  font-size: 10px;
}

a {
  text-decoration: none;
  color: #fff;
}

a:hover {
  color: #2ecc71;
}

.main {
  width: 100%;
  padding: 1rem 0rem 3rem;

}

.sub-main {
  width: 30%;
  margin: 22px;
  align-self: center;
  float: left;
}
.sub-main2 {
  width: 100%;
  margin: -30px;
}

.button-one,
.button-two,
.button-three {
  text-align: center;
  cursor: pointer;
  font-size: 13px;
  margin: 0 0 0 80px;
}

/*Button One*/
.button-one {
  padding: 10px 30px;
  outline: none;
  background-color: #27ae60;
  border: none;
  border-radius: 5px;
  box-shadow: 0 9px #95a5a6;
}

.button-one:hover {
  background-color: #2ecc71;
}

.button-one:active {
  background-color: #2ecc71;
  box-shadow: 0 5px #95a5a6;
  transform: translateY(4px);
}

/*Button Two*/
.button-two {
  border-radius: 4px;
  background-color: #d35400;
  border: none;
  padding: 20px;
  width: 200px;
  transition: all 0.5s;
}

.button-two span {
  cursor: pointer;
  display: inline-block;
  position: relative;
  transition: 0.5s;
}

.button-two span:after {
  content: "»";
  position: absolute;
  opacity: 0;
  top: 0;
  right: -20px;
  transition: 0.5s;
}

.button-two:hover span {
  padding-right: 25px;
}

.button-two:hover span:after {
  opacity: 1;
  right: 0;
}

/*Button Three*/
.button-three {
  position: relative;
  background-color: #f39c12;
  border: none;
  padding: 20px;
  width: 200px;
  text-align: center;
  -webkit-transition-duration: 0.4s; /* Safari */
  transition-duration: 0.4s;
  text-decoration: none;
  overflow: hidden;
}

.button-three:hover {
  background: #fff;
  box-shadow: 0px 2px 10px 5px #97b1bf;
  color: #000;
}

.button-three:after {
  content: "";
  background: #f1c40f;
  display: block;
  position: absolute;
  padding-top: 300%;
  padding-left: 350%;
  margin-left: -20px !important;
  margin-top: -120%;
  opacity: 0;
  transition: all 0.8s;
}

.button-three:active:after {
  padding: 0;
  margin: 0;
  opacity: 1;
  transition: 0s;
}
</style>
