<template>
  <div>
    <div class="blank" />
    <div class="wrapper">
      <div class="img1" />
      <h2 class="title1">Lorem ipsum<br /><span>Dolor sit amet.</span></h2>
      <div class="img2" />
      <h2 class="title2">Lorem ipsum<br />dolor sit amet.</h2>
    </div>
    <div class="blank" />
  </div>
</template>

<script>
import { gsap } from "gsap";

export default {
  mounted: function() {
    this.startAnimations();
  },
  methods: {
    startAnimations: function() {
      gsap.to("#title", { duration: 1, color: "red" });
    }
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Nunito+Sans&display=swap");

$black: #000;
$white: #fff;

*,
*::before,
*::after {
  box-sizing: inherit;
  padding: 0;
  margin: 0;
}

html {
  box-sizing: border-box;
  font-size: 62.5%;
}

body {
  width: 100%;
  -webkit-font-smoothing: antialiased;
  font-family: "Nunito Sans", sans-serif;
  overflow-x: hidden;
  color: $black;
}

.blank {
  width: 100%;
  height: 100vh;
}

.wrapper {
  background: red;
  width: 100%;
  height: 100vh;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: flex-end;
  overflow: hidden;

  .img1 {
    background-image: url("../assets/img/scroll.jpg");
    width: 60%;
    height: 60%;
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center center;
  }

  .title1 {
    position: absolute;
    top: 50%;
    left: 20%;
    font-size: 4rem;
    transform: translate(-50%, -50%);
    color: $white;
    opacity: 0;
    span {
      font-size: 3rem;
      font-weight: 400;
      display: block;
    }
  }

  .img2 {
    background-image: url("../assets/img/scroll2.jpg");
    position: absolute;
    width: 100%;
    height: 0;
    left: 50%;
    bottom: 0;
    transform: translate(-50%, 0);
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center bottom;
  }

  .title2 {
    position: absolute;
    top: 50%;
    left: 50%;
    font-size: 6rem;
    transform: translate(-50%, -50%);
    color: $white;
    transform-origin: center center;
    text-align: center;
    line-height: 6rem;
    span {
      font-size: 3rem;
      font-weight: 400;
      display: block;
    }
  }
}
</style>
