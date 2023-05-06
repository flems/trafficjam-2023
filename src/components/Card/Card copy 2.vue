<template>

  <div class="clip-each box-shadow-inset">
  </div>	

		<svg class="clip-svg">
			<defs>
				<clipPath id="octagon-clip" clipPathUnits="objectBoundingBox">
					<polygon points="0.3 0, 0.7 0, 1 0.3, 1 0.7, 0.7 1, 0.3 1, 0 0.7, 0 0.3" />
				</clipPath>
			</defs>
		</svg>	

</template>

<script setup>
</script>

<style lang="scss">

.clip-svg {
  width: 0;
  height: 0;
}

.clip-each {
  width: 180px;
  height: 180px;
  position: relative;
  margin: 50px;
  transition: all 0.2s;
  background: #fff;

  &:after {
    content: "21313";
    position: absolute;
    background: green;
    width: calc(100% - 4px);
    height: calc(100% - 4px);
    top: 2px;
    left: 2px;
  }

  &:hover {
    background-color: red;
    filter: blur(3px);
  }
}


.clip-each,
.clip-each:after {
  -webkit-clip-path: polygon(30% 0, 70% 0, 100% 30%, 100% 70%, 70% 100%, 30% 100%, 0 70%, 0 30%);
  clip-path: polygon(30% 0, 70% 0, 100% 30%, 100% 70%, 70% 100%, 30% 100%, 0 70%, 0 30%);
  clip-path: url("#octagon-clip");
}

// .box-shadow-inset {	
//   background-color: rgba(0,0,0,0.15);
//   // filter: blur(3px);
// }

// .box-shadow-inset:after {	
//   background: #fff;
//   top: 4px;
//   left: 4px;
//   right: 4px;
//   bottom: 4px;
// }

</style>
