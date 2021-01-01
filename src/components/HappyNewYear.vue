<template>
  <div class="new-year-message tracking-in-contract">
    <div class="tagLine rainbow-text">Happy New Year</div>
    <div class="year">{{ year }}</div>
  </div>
</template>

<script>
export default {
  name: "HappyNewYear",
  props: ["year"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.new-year-message {
  font-size: 5rem;
  position: fixed;
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  text-align: center;
  align-items: center;
  width: 100%;
  height: 100%;
  z-index: -1;
}

.rainbow-text {
  background-image: linear-gradient(
    to left,
    violet,
    indigo,
    blue,
    green,
    yellow,
    orange,
    red
  );
  color: transparent;
  background-clip: text;
}

.tracking-in-contract {
  -webkit-animation: tracking-in-contract 6s cubic-bezier(0.215, 0.61, 0.355, 1)
    alternate-reverse infinite;
  animation: tracking-in-contract 6s cubic-bezier(0.215, 0.61, 0.355, 1)
    alternate-reverse infinite;
}

@-webkit-keyframes tracking-in-contract {
  0% {
    letter-spacing: 1em;
    opacity: 0;
  }
  20% {
    opacity: 0.4;
  }
  40% {
    opacity: 0.6;
  }
  100% {
    letter-spacing: normal;
    opacity: 1;
  }
}

@keyframes tracking-in-contract {
  0% {
    letter-spacing: 1em;
    opacity: 0;
  }
  20% {
    opacity: 0.4;
  }
  40% {
    opacity: 0.6;
  }
  100% {
    letter-spacing: normal;
    opacity: 1;
  }
}
</style>
