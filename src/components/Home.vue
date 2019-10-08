<template>
  <div>
    <Navbar />
    <header class="header">
      <div class="header-side">
        <h4>Find Github users repos!</h4>
        <Search :query="query" :submitHandler="submitHandler" :changeHandler="changeHandler" />
      </div>
      <img src="/images/search.png" alt="person with magnifying glass" />
    </header>
    <main>
      <section v-if="user" class="main">
        <div v-if="user.length !== 0">
          <h2>Check out {{user[0].owner.login}}'s Repos</h2>
          <Card v-for="(repo, idx) in user" :key="idx" :repo="repo" />
        </div>
        <div v-else>
          <Validation>
            <img src="/images/empty_boxes.png" alt="Not found" />
            <p>This user has no repositories!</p>
          </Validation>
        </div>
      </section>
      <Validation v-if="error">
        <img src="/images/bunny-error.png" alt="error" />
        <p>Sorry, We couldn't find that user! Are you sure you typed that right?</p>
      </Validation>
      <Loader v-if="loading" />
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Navbar from "./Navbar";
import Search from "./Search";
import Card from "./Card";
import Validation from "./validation/Validation";
import Loader from "./validation/Loader";

export default {
  name: "Home",
  components: {
    Navbar,
    Search,
    Card,
    Validation,
    // Error,
    // NotFound,
    Loader
  },
  data() {
    return {
      user: null,
      query: "",
      error: false,
      loading: false
    };
  },
  methods: {
    submitHandler: function() {
      this.loading = true;

      axios
        .get(`https://api.github.com/users/${this.query}/repos`)
        .then(res => {
          this.user = res.data;
          this.query = "";
          this.loading = false;
          this.error = false;
        })
        .catch(() => {
          this.user = null;
          this.query = "";
          this.loading = false;
          this.error = true;
        });
    },
    changeHandler: function(e) {
      this.query = e.target.value;
    }
  }
};
</script>

<style scoped lang="scss">
@import "../scss/mixins.scss";
@import "../scss/variables.scss";

.header {
  @include flexCenter(space-around);
  flex-wrap: wrap;
  height: auto;
  padding: 4rem 1rem 0px 1rem;
  background-color: $backgroundHeader;

  img {
    height: 25vw;
  }

  .header-side {
    @include flexCenter(center);
    flex-direction: column;
    h4 {
      text-transform: uppercase;
      letter-spacing: 3px;
      font-size: 1.4em;
      text-align: center;
    }
  }
}

.main {
  @include flexCenter(center);
  flex-direction: column;
  padding-top: 2rem;
  padding-bottom: 4rem;

  h2 {
    text-transform: uppercase;
  }
}

@media (min-width: 601px) and (max-width: 1020px) {
  .header {
    img {
      height: 40vw;
    }
  }
}

@media (max-width: 600px) {
  .header {
    img {
      height: 50vw;
    }
  }

  .main {
    h2 {
      text-align: center;
    }
  }
}
</style>
