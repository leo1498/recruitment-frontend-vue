<template>
   <div class="search" data-bg="Search">
      <input 
         type="search" 
         v-bind:search="search"
         v-on:input="$emit('input', $event.target.value)"
         placeholder=" "
         autocomplete="off"
         id="searchInput" 
      >
      <label for="searchInput">Search...</label>
      <span class="line-ripple"></span>
   </div>     
</template>

<script>
export default {
   name: "FeedPreviewSearchTpl",
   props: ["search"]
};
</script>

<style lang="scss" scoped>
.search{
   max-width: 480px;
   width: 100%;
   margin: 100px auto 70px;
   position: relative;

   &::before{
      content: attr(data-bg);
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translateX(-50%);
      font-size: 20rem;
      color: rgba(0,0,0,.03);
      line-height: 0;
      font-weight: 900;
      letter-spacing: 5px;
      letter-spacing: 5px;
      z-index: -1;
   }

   label{
      position: absolute;
      top: 15px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 3rem;
      font-weight: 100;
      letter-spacing: 1px;
      color: #93A4B1;
      transition: transform .25s ease-in-out, color .25s ease-in-out;
   }

   input{
      width: 100%;
      padding: 15px 5px;
      border: none;
      background-color: transparent;
      border-bottom: 2px solid #AFC4D3;
      border-radius: 0;
      outline: none;
      text-align: center;
      font-weight: 700;
      font-size: 3rem;
      position: relative;
      -webkit-appearance: none;

      &:not(:placeholder-shown) + label,
      &:focus + label{
         transform: translate(-50%, calc(-100% - 1rem)) scale(.7);
         color: #5D86DE;
      }

      &:focus ~ .line-ripple{
         transform: scaleX(1);
      }
   }

   .line-ripple{
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 2px;
      background-color: #5D86DE;
      transform: scaleX(0);
      transform-origin: center;
      transition: transform .5s ease-in-out;
   }
}
</style>
