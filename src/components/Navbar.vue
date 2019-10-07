<template>
  <nav>
    <div class="logo">
      <h4>GitHub Search</h4>
    </div>
    <a href="https://github.com/">Official GitHub</a>
  </nav>
</template>

<script>
export default {
  name: "Navbar"
};
</script>

<style scoped lang="scss">
@import "../scss/mixins.scss";
@import "../scss/variables.scss";

nav {
  @include flexCenter(space-around);
  background-color: $backgroundNavbar;
  a {
    text-decoration: none;
    letter-spacing: 1px;
    color: black;
  }
}

.logo {
  h4 {
    text-transform: uppercase;
    letter-spacing: 5px;
  }
}

@media (max-width: 600px) {
  nav {
    a {
      display: none;
    }
  }
}
</style>
