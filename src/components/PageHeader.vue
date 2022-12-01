<template>
   <div>
    <h1>BOOLFLIX</h1>
    <form @submit.prevent="$emit('search',searchString)">
      <label for="g">
         <input
         type="text"
         id="g"
         v-model="searchString"
         name="g"
         placeholder=" Cerca serie o film"
         >
      </label>
      <button>
         Cerca
      </button>
    </form>
   </div>
</template>

<script>
export default {
  name: 'PageHeader',
  data() {
    return {
      searchString: '',
    };
  },
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
      form{
        padding-right: 2em;
        align-self: center;
        label{
          margin: auto;
          height: 2em;
        }
        button{
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
