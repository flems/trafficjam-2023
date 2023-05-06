<template>
  <div class="card">
    <div class="card__content">
      123123132
    </div>
      <!-- <svg class="svg">
        <clipPath id="my-clip-path" clipPathUnits="objectBoundingBox"><path d="M-0.005,0.069 V0.92 H0.005 V0.069 H-0.005 M0.059,-0.006 C0.024,-0.006,-0.005,0.028,-0.005,0.069 H0.005 C0.005,0.034,0.029,0.006,0.059,0.006 V-0.006 M0.468,-0.006 H0.059 V0.006 H0.468 V-0.006 M0.931,0.121 H0.577 V0.132 H0.931 V0.121 M0.995,0.92 V0.195 H0.985 V0.92 H0.995 M0.931,0.994 C0.966,0.994,0.995,0.961,0.995,0.92 H0.985 C0.985,0.954,0.961,0.983,0.931,0.983 V0.994 M0.059,0.994 H0.931 V0.983 H0.059 V0.994 M-0.005,0.92 C-0.005,0.961,0.024,0.994,0.059,0.994 V0.983 C0.029,0.983,0.005,0.954,0.005,0.92 H-0.005 M0.931,0.132 C0.961,0.132,0.985,0.16,0.985,0.195 H0.995 C0.995,0.154,0.966,0.121,0.931,0.121 V0.132 M0.517,0.063 C0.517,0.101,0.544,0.132,0.577,0.132 V0.121 C0.549,0.121,0.527,0.095,0.527,0.063 H0.517 M0.468,0.006 C0.495,0.006,0.517,0.031,0.517,0.063 H0.527 C0.527,0.025,0.501,-0.006,0.468,-0.006 V0.006"></path></clipPath>
      </svg>

      <div class="clipped"></div> -->
  </div>
</template>

<script setup>
</script>

<style lang="scss">
.svg {
  position: absolute;
  width: 0;
  height: 0;
}

.clipped {
  width: 100%;
  height: 350px;
  // background-size: cover;
  // -webkit-clip-path: url(#my-clip-path);
  clip-path: path('M0 320V24C0 10.7452 10.7452 0 24 0H189C201.15 0 211 9.84974 211 22V22C211 34.1503 220.85 44 233 44H376C389.255 44 400 54.7452 400 68V320C400 333.255 389.255 344 376 344H24C10.7452 344 0 333.255 0 320Z');
}


.card {
  // temp
  width: 400px;
  height: 350px;
  margin: 50px;
  position: relative;
  // outline: 1px solid #fff;

  // /temp

  &__content {
    height: 100%;
    width: 100%;
    padding-top: calc(44px + 20px);
    padding-left: 32px;
    padding-right: 32px;
  }

  &:before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: red;
    clip-path: path('M-2 24V320H2V24H-2ZM24 -2C9.64059 -2 -2 9.64059 -2 24H2C2 11.8497 11.8497 2 24 2V-2ZM189 -2H24V2H189V-2ZM376 42H233V46H376V42ZM402 320V68H398V320H402ZM376 346C390.359 346 402 334.359 402 320H398C398 332.15 388.15 342 376 342V346ZM24 346H376V342H24V346ZM-2 320C-2 334.359 9.64059 346 24 346V342C11.8497 342 2 332.15 2 320H-2ZM376 46C388.15 46 398 55.8497 398 68H402C402 53.6406 390.359 42 376 42V46ZM209 22C209 35.2548 219.745 46 233 46V42C221.954 42 213 33.0457 213 22H209ZM189 2C200.046 2 209 10.9543 209 22H213C213 8.74517 202.255 -2 189 -2V2Z');
    width: 100%;
    height: 100%;
  }

  // &:after {
  //   background: green;
  //   width: calc(100% - 4px);
  //   height: calc(100% - 6px);
  //   top: 2px;
  //   left: 2px;
  // }

  // border-radius: 0 0 24px 24px;
  // background: #000210;
  // border: 2px solid #6B6B6B;
  // border-top: none;
  // position: relative;
  // // box-shadow: inset 0 0 0 2px #6B6B6B;
  // padding-top: 44px;
 

  // &:before {
  //   content: '';
  //   width: calc(100% - 190px);
  //   height: 44px;
  //   display: block;
  //   position: absolute;
  //   bottom: 100%;
  //   left: -2px;
  //   border: 2px solid #6B6B6B;
  //   border-radius: 24px 24px 0 0;

  // }
}
</style>
