<template>
   <div class="fetch-data-error">
      <span>
         Error! Something is wrong: 
         <pre>{{ dataErrMsg }}</pre>
      </span>
      <button class="btn" @click="reloadPage">Try again</button>
   </div>
</template>

<script>
export default {
   props: ["dataErrMsg"],
   methods: {
      // Instead of calling a method to get data from the server, I reload the page
      reloadPage() {
         window.location.reload();
      }
   }
}
</script>

<style lang="scss" scoped>
.fetch-data-error{
   display: flex;
   align-items: center;
   flex-direction: column;

   span{
      display: inline-block;
      width: 100%;
      max-width: 480px;
      margin: 30px 0;
      padding: 20px 30px;
      background-color: #eee;
      color: #222;
      font-weight: 300;
      text-align: center;

      pre{
         margin-top: 10px;
         color: #DC5151;
         white-space: pre-wrap;    
         white-space: -moz-pre-wrap;
         white-space: -pre-wrap;
         white-space: -o-pre-wrap;
         word-wrap: break-word;     
      }
   }

   .btn{
      display: block;
      border: none;
      outline: none;
      background-color: #DC5151;
      padding: 20px 40px;
      text-align: center;
      color: #fff;
      font-size: 2rem;
      border-radius: 7px;
      cursor: pointer;
      transition: opacity .25s ease-in-out;

      &:hover{
         opacity: .9;
      }
   }
}
</style>