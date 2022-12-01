<template>
   <div>
    <h1>BOOTFLIX</h1>
    <div>
      <label for="g">
         <input
         type="text"
         id="g"
         v-model="searchString"
         name="g"
         placeholder="Cerca serie o film"
         >
      </label>
      <button>
         Cerca
      </button>
    </div>
   </div>
</template>

<script>
export default {

};
</script>

<style lang="scss" scoped>
    div{
      display: flex;
      justify-content: space-between;
      height: 10vh;
      background-color: black;
      h1{
        color: red;
        align-self: center;
        padding-left: 2em;
      }
      div{
        padding-right: 2em;
        label{
          margin: auto;
          height: 2em;
        }
        button{
          margin: auto;
          height: 1.9em;
          font-size: .9em;
          background-color: gray;
          border-radius: 15px;
          margin-left:1em;
          padding: 0 .5em;
          border: 1px solid red;
        }
      }
    }
</style>
