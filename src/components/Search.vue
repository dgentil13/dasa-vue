<template>
  <div class="search">
    <form @submit.prevent="submitHandler" class="search-input">
      <input
        type="text"
        @change="changeHandler"
        :value="query"
        placeholder="Search for a GitHub user!"
      />
      <button type="submit">
        <img src="/images/search-solid.svg" alt="magnifying glass" />
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Search",
  props: {
    submitHandler: Function,
    changeHandler: Function,
    query: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../scss/mixins.scss";

.search {
  padding: 1rem;
  form {
    display: flex;
    justify-content: center;
  }
}

.search-input {
  input {
    border: none;
    border-bottom: 3px solid black;
    height: 7vh;
    width: 40vh;
    padding: 5px 5px 0px 5px;
    font-size: 1.4rem;

    &:focus {
      outline: none;
    }
  }

  button {
    background-color: white;
    border: none;
    border-bottom: 3px solid black;
    cursor: pointer;

    img {
      height: 30px;
    }

    &:focus {
      outline: none;
    }
  }
}

@media (max-width: 600px) {
  .search-input {
    input {
      width: 100%;
    }
  }
  .clicked-search {
    input {
      width: 100%;
    }
  }
}
</style>
