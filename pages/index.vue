<template>
  <div>
    <div class="blank" />
    <div class="navbar">
      <h1>
        Apple scroll
      </h1>
      <ul>
        <li>Product</li>
        <li>About Us</li>
        <li>Buy</li>
      </ul>
    </div>
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
      let tl = new TimelineMax({ onUpdate: udpatePourcentage });

      tl.to(".img1", 1, { width: "100%", height: "100%" }, 0);
      tl.to(".title1", 0.5, { opacity: 1 }, 1);
      tl.to(".title1", 0.5, { opacity: 0 }, 2);
      tl.to(".img2", 1, { height: "100%" }, 2);
      tl.from(".title2", 1, { opacity: 0 }, 2.2);
      tl.to(".img1", 0, { opacity: 0 }, 3);
      tl.to(
        ".img2",
        1,
        {
          width: "60%",
          height: "60%",
          transform: "translate(-30%, -30%)"
        },
        3
      );
      tl.to(".title2", 1, { color: "rgba(0,0,0,0)" }, 3);

      const scene = this.$scrollmagic
        .scene({
          triggerElement: ".wrapper",
          triggerHook: 0,
          duration: "300%"
        })
        .setPin(".wrapper")
        .setTween(tl);

      this.$scrollmagic.addScene(scene);

      function udpatePourcentage() {
        tl.progress();
      }
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
  scroll-behavior: smooth;
}

body {
  width: 100%;
  -webkit-font-smoothing: antialiased;
  font-family: "Nunito Sans", sans-serif;
  overflow-x: hidden;
  color: $black;
}

.navbar {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  justify-content: space-between;
  width: 100%;
  padding: 2rem;
  border-bottom: 1px solid $black;
  background-color: $white;
  z-index: 10;

  h1 {
    font-size: 3rem;
    font-weight: 300;
    text-transform: uppercase;
  }

  ul {
    display: flex;
    justify-content: space-around;
    width: 20%;
    list-style: none;
    align-items: center;
    font-size: 1.7rem;
    font-weight: 700;

    ul:last-child {
      border: 1px solid $black;
    }
  }
}
.blank {
  width: 100%;
  height: 100vh;
}

.wrapper {
  // background: red;
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
    top: 60%;
    right: 10%;
    font-size: 5rem;
    transform: translate(-50%, -50%);
    color: $white;
    opacity: 0;
    mix-blend-mode: difference;
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
    font-size: 8rem;
    transform: translate(-50%, -50%);
    color: $white;
    transform-origin: center center;
    text-align: center;
    line-height: 8rem;
    mix-blend-mode: difference;
    span {
      font-size: 3rem;
      font-weight: 400;
      display: block;
    }
  }
}
</style>
