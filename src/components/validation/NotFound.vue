<template>
  <div class="not-found">
    <img src="/images/empty_boxes.png" alt="Not found" />
    <p>This user has no repositories!</p>
  </div>
</template>

<script>
export default {
  name: "NotFound"
};
</script>

<style scoped lang="scss">
@import "../../scss/mixins.scss";

.not-found {
  padding: 3rem 3rem 7rem 3rem;
  @include flexCenter(center);
  flex-wrap: wrap;

  img {
    height: 40vh;
  }

  p {
    font-size: 1.5rem;
    font-weight: 600;
    width: 50vh;
    text-align: center;
    text-transform: uppercase;
  }
}

@media (max-width: 600px) {
  .not-found {
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
