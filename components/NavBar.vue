<template>
<div>
  <nav class="navbar is-fixed-top" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item" href="https://bulma.io">
        <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28">
      </a>

      <a role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div id="navbarBasicExample" class="navbar-menu">
      <div class="navbar-start">
        <a class="navbar-item" v-for="link in menuByName.links" v-bind:key="link" :href="link.url.path" v-html="link.label"/>

        <div class="navbar-item has-dropdown is-hoverable">
          <a class="navbar-link">
            More
          </a>

          <div class="navbar-dropdown">
            <a class="navbar-item" href="/about">
              About
            </a>
            <a class="navbar-item" href="/contact-us">
              Contact Us
            </a>
            <hr class="navbar-divider">
            <a class="navbar-item">
              Report an issue
            </a>
          </div>
        </div>
      </div>

      <div class="navbar-end">
        <div class="navbar-item">
          <div class="buttons">
            <a class="button is-primary">
              <strong>Sign up</strong>
            </a>
            <a class="button is-light">
              Log in
            </a>
          </div>
        </div>
      </div>
    </div>
  </nav>
</div>
</template>

<script>
import menuQuery from "~/queries/menuQuery.gql";

export default {
  data() {
    return {};
  },
  // mounted() {
  //   this.getMenu()
  // },
  // methods: {
  //   getMenu(){
  //     console.log('gettin it')
  //     const client = this.$apollo.getClient()
  //     let variables = {name: "main"}
  //     this.$apollo.query({query: menuQuery, variables: this.variables})
  //       .then(({ data }) => {
  //         // do what you want with data
  //         console.log('yo', data)
  //       })
  //   }
  // }
  apollo: {
    menuByName: {
      prefetch: true,
      query: menuQuery,
      variables() {
        return {
          name: "main"
        };
      }
    }
  }
}
</script>

<style>
pre {
  margin-top: 3rem; 
}
</style>