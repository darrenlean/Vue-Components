<template>
<div>
  <div class="progress-bar-container">
    <div class="progress-bar stripes animated reverse slower">
      <span class="progress-bar-inner" v-bind:style="moveProgress"></span>
    </div>
  </div>
</div>
</template>

<script>
export default {
    name:"iv-loading-bar",
    props: {
      loadingProgress: {
        type: Number,
        default: 0
      }
    },
    computed: {
      moveProgress: function () {
        return {
          width: this.loadingProgress + "%"
        }
      }
    }
}
</script>

<style scoped>
body, html {
  height: 100%;
  background: #333344;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

@keyframes animate-stripes {
    0% {
        background-position: 0 0;
    }

    100% {
        background-position: 60px 0;
    }
}

.progress-bar {
    background-color: #302f2f;
    height: 3vh;
    width: 35vw;
    margin: 50px auto;
    border-radius: 5px;
    box-shadow: 0 1px 5px rgb(44, 44, 44) inset, 0 1px 0 #bcbdbc;
}

.stripes {
    background-size: 30px 30px;
    background-image: linear-gradient(
        135deg,
        rgba(255, 255, 255, .15) 25%,
        transparent 25%,
        transparent 50%,
        rgba(255, 255, 255, .15) 50%,
        rgba(255, 255, 255, .15) 75%,
        transparent 75%,
        transparent
    );
}

.stripes.animated {
  animation: animate-stripes 0.6s linear infinite;
}

.stripes.animated.slower {
  animation-duration: 1.25s;
}

.stripes.reverse {
  animation-direction: reverse;
}

.progress-bar-inner {
  display: block;
  height: 3vh;
  width: 0%;
  background-color: #3498db;
  border-radius: 3px;
  box-shadow: 0 1px 0 rgba(255, 255, 255, .5) inset;
  position: relative;
  animation: auto-progress 10s infinite linear;
}
</style>