<template>
  <div class="error">
    <img src="/images/bunny-error.png" alt="error" />
    <p>Sorry, We couldn't find that user! Are you sure you typed that right?</p>
  </div>
</template>

<script>
export default {
  name: "Error"
};
</script>

<style scoped lang="scss">
@import "../../scss/mixins.scss";

.error {
  @include flexCenter(center);
  flex-wrap: wrap;
  padding: 3rem 3rem 7rem 3rem;

  img {
    height: 40vh;
  }

  p {
    font-size: 1.5em;
    font-weight: 600;
    width: 30vw;
    text-align: center;
    text-transform: uppercase;
  }
}

@media (max-width: 600px) {
  .error {
    padding: 0px 0px 7rem 0px;

    img {
      height: 25vh;
    }

    p {
      font-size: 1rem;
      width: 30vh;
    }
  }
}
</style>
