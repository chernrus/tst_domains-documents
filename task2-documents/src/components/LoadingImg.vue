<template>
  <div class="spinner">
  	<div class="spinner__circle">
  		<div class="spinner__circle-gradient"></div>

  		<div class="spinner__circle-inner"></div>
  	</div>
  </div>
</template>

<script>
export default {
  name: 'LoadingImg'
}
</script>

<style lang="scss" scoped>
$primaryColor: #5F6062;
$secondaryColor: #fff;

@keyframes spin {
100% {
  transform: rotate(360deg);
}
}

* {
box-sizing: border-box;
padding: 0;
margin: 0;
text-rendering: optimizeLegibility;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
-webkit-tap-highlight-color: rgba(0,0,0,0);
}

.spinner {
// position: absolute;
// top: 50%;
// left: 50%;
// transform: translate(-50%, -50%);

&__circle {
  position: relative;
  width: 32px;
  height: 32px;
  overflow: hidden;
  background-color: $primaryColor;
  border-radius: 100%;
  animation: spin 1s infinite linear;

  &-inner,
  &-gradient {
    position: absolute;
    width: 44px;
    height: 44px;
    transform: translate(-50%, -50%);
  }

  &-inner {
    top: 50%;
    left: 50%;
    background-color: $secondaryColor;
    border-radius: 100%;
  }

  &-gradient {
    top: -24px;
    left: 6px;
    background-color: $primaryColor;
    background-image:    -moz-linear-gradient(0deg,$primaryColor 0%,$secondaryColor 50%);
    background-image: -webkit-linear-gradient(0deg,$primaryColor 0%,$secondaryColor 50%);
    background-image:         linear-gradient(0deg,$primaryColor 0%,$secondaryColor 50%);
    transform: rotate(-45deg);
  }
}
}
</style>
