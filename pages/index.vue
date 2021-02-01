<template>
  <div>
    <h1 id="title">
      Hello World
    </h1>
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

<style></style>
