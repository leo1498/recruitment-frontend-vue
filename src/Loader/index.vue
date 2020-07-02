<template>
   <div class="loader-spinner">
      <div class="loader-spinner__circle"></div>
   </div>
</template>

<style lang="scss" scoped>
.loader-spinner{
   padding: 30px 0;
   text-align: center;
   
   &__circle{
      display: inline-block;
      width: 80px;
      height: 80px;

      &:after{
         content: "";
         display: block;
         width: 64px;
         height: 64px;
         margin: 8px;
         border-radius: 50%;
         border: 6px solid #5D86DE;
         border-color: #5D86DE transparent #5D86DE transparent;
         animation: loader-spinner 1.2s linear infinite;
      }
   }
}

@keyframes loader-spinner {
   0% {
      transform: rotate(0);
   }
   100% {
      transform: rotate(360deg);
   }
}
</style>