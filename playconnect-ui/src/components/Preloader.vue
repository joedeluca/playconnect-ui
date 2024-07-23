<template>
  <div class="loader"></div>
</template>
<style scoped>
/* .loader {
  width: 65px;
  height: 117px;
  position: relative;
}
.loader:before,
.loader:after {
  content: "";
  position: absolute;
  inset: 0;
  background: #16a34a;
  box-shadow: 0 0 0 50px;
  clip-path: polygon(
    100% 0,
    23% 46%,
    46% 44%,
    15% 69%,
    38% 67%,
    0 100%,
    76% 57%,
    53% 58%,
    88% 33%,
    60% 37%
  );
}
.loader:after {
  animation: l8 1s infinite;
  transform: perspective(300px) translateZ(0px);
}
@keyframes l8 {
  to {
    transform: perspective(300px) translateZ(180px);
    opacity: 0;
  }
} */
/* HTML: <div class="loader"></div> */
/* .loader {
  width: 20px;
  aspect-ratio: 1;
  border-radius: 50%;
  background: #000;
  box-shadow: 0 0 0 0 #0004;
  animation: l2 1.5s infinite linear;
  position: relative;
}
.loader:before,
.loader:after {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: inherit;
  box-shadow: 0 0 0 0 #0004;
  animation: inherit;
  animation-delay: -0.5s;
}
.loader:after {
  animation-delay: -1s;
}
@keyframes l2 {
  100% {
    box-shadow: 0 0 0 40px #0000;
  }
} */

/* HTML: <div class="loader"></div> */
/* .loader {
  width: 60px;
  aspect-ratio: 1;
  position: relative;
}
.loader:before,
.loader:after {
  content: "";
  position: absolute;
  border-radius: 50%;
  inset: 0;
  background: radial-gradient(circle 10px, #15803d 94%, #0000),
    repeating-conic-gradient(from -30deg, #0000 0 60deg, #15803d 61deg 120deg);
  -webkit-mask: radial-gradient(
    circle 15px,
    #000 calc(100% - 6px),
    #0000 calc(100% - 5px) 94%,
    #000
  );
}
.loader:after {
  animation: l4 1s infinite;
  transform: perspective(300px) translateZ(0px);
}
@keyframes l4 {
  to {
    transform: perspective(300px) translateZ(150px);
    opacity: 0;
  }
} */
.loader {
  width: 40px;
  aspect-ratio: 1;
  position: relative;
  transform: rotate(45deg);
}
.loader:before,
.loader:after {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: 50% 50% 0 50%;
  background: #16a34a;
  -webkit-mask: radial-gradient(circle 10px at 50% 50%, #0000 94%, #000);
  mask: radial-gradient(circle 10px at 50% 50%, #0000 94%, #000);
}
.loader:after {
  animation: l6 1s infinite;
  transform: perspective(300px) translateZ(0px);
}
@keyframes l6 {
  to {
    transform: perspective(300px) translateZ(150px);
    opacity: 0;
  }
}
</style>
