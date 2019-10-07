<template>
  <div class="loading">
    <p>... Loading</p>
  </div>
</template>

<script>
export default {
  name: "Loader"
};
</script>

<style scoped lang="scss">
@import "../../scss/mixins.scss";

.loading {
  @include flexCenter(center);
  flex-wrap: wrap;
  padding: 3rem 3rem 7rem 3rem;

  p {
    font-size: 1.5em;
    font-weight: 600;
    width: 30vw;
    text-align: center;
    text-transform: uppercase;
  }

  @media (max-width: 600px) {
    .loading {
      padding: 0px 0px 7rem 0px;

      p {
        font-size: 1rem;
        width: 30vh;
      }
    }
  }
}
</style>
