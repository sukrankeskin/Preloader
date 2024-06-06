<template>
  <div>
    <div class="website-content">
      <div class="header">
        <div class="h1">
          <h1>Website</h1>
          <h1>Content</h1>
        </div>
        <div class="header-revealer"></div>
      </div>
    </div>
    <div class="loading-screen">
      <div class="loader">
        <img class="logo" src="./assets/logo.svg" alt="" />
        <!-- Yeni yükleyici -->
      </div>
    </div>
  </div>
</template>

<script>
import { gsap } from "gsap";

export default {
  name: "App",
  mounted() {
    this.initCounter();
    this.initAnimations();
  },
  methods: {
    initCounter() {
      function animate(counter, duration, delay = 0) {
        const numHeight = counter.querySelector(".num").clientHeight;
        const totalDistance =
          (counter.querySelectorAll(".num").length - 1) * numHeight;
        gsap.to(counter, {
          y: -totalDistance,
          duration: duration,
          delay: delay,
          ease: "power2.inOut",
        });
      }
    },
    initAnimations() {
      gsap.to(".digit", {
        top: "-150px",
        stagger: {
          amount: 0.25,
        },
        delay: 1,
        duration: 1,
        ease: "power4.inOut",
      });

      gsap.from(".logo", {
        opacity: 0,
        duration: 1,
        ease: "power2.inOut",
      });

      gsap.to(".logo", {
        rotate: 360,
        y: -10,
        opacity: 1,
        duration: 0.5,
        delay: 1,
      });

      gsap.to(".loader", {
        scale: 600,
        duration: 1,
        delay: 2,
        ease: "power2.inOut",
      });

      gsap.to(".loader", {
        rotate: 45,
        y: 500,
        x: 2000,
        duration: 1,
        delay: 3,
        ease: "power2.inOut",
      });

      gsap.to(".loading-screen", {
        opacity: 0,
        duration: 0.5,
        delay: 2,
        ease: "power1.inOut",
      });

      gsap.to("h1", 1.5, {
        delay: 2,
        y: -80,
        ease: "power4.inOut",
        stagger: {
          amount: 0.1,
        },
      });
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html,
body {
  width: 100vw;
  height: 100vh;
  font-family: "Aeonik_OVERVIEW";
}

.loading-screen {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: #000;
  color: #fff;
  pointer-events: none;
}

.loader {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 300px;
  height: 50px;
  transform: translate(-50%, -50%);
  display: flex;
  align-items: center;
  justify-content: center;
}

.website-content {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.header {
  position: relative;
  width: max-content;
  height: max-content;
}

.h1 {
  display: flex;
}

h1 {
  font-size: 80px;
}

.header .h1 h1 {
  text-align: center;
  position: relative;
  top: 80px;
  margin: 0 10px;
  text-transform: uppercase;
  font-weight: 400;
}

.header-revealer {
  position: absolute;
  top: 0;
  width: 100%;
  height: 100%;
}

.header-revealer:after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 105%;
  height: 110%;
  background: #fff;
  top: 80px;
}
</style>
