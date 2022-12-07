<template>
  <header>
    <h1>BOOLFLIX</h1>
    <form @submit.prevent="$emit('queryChange', queryString)">
      <label for="query">
        <input
          id="query"
          v-model="queryString"
          type="text"
          name="query"
        >
      </label>
      <button>Cerca</button>
    </form>
  </header>
</template>

<script>
export default {
  name: 'PageHeader',
  data() {
    return {
      queryString: '',
    };
  },
};
</script>

<style lang="scss" scoped>
  header{
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
