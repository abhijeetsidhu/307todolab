<template>
  <div id="app">
    <div class="navbar">
      <div class="navbar-menu">
        <div class="navbar-start">
          <router-link class="navbar-item is-tab" to="/" exact-active-class="is-active">Home</router-link> 
          <router-link class="navbar-item is-tab" to="/about" exact-active-class="is-active">About</router-link>
          <router-link class="navbar-item is-tab" to="/todos" exact-active-class="is-active">Todos</router-link>
        </div>
        <div class="navbar-end">
          <div class="navbar-item">
            <div class="buttons">
              <a class="button is-primary" v-on:click="showSignupModal()">
                <strong>Sign up</strong>
              </a>
              <a class="button is-light" v-on:click="showLoginModal()">
                Log in
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <router-view/>
    <Signup v-bind:is-showing="showSignup" v-on:success="successSignup()" v-on:cancel="cancelSignup()"/>
    <Login v-bind:is-showing="showLogin" v-on:success="successLogin()" v-on:cancel="cancelLogin()"/>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import { Component } from "vue-property-decorator";
import Signup from "@/components/Signup.vue";
import Login from "@/components/Login.vue";

@Component({
  components: {
    Signup,
    Login
  }
})
export default class App extends Vue {
  public showSignup: boolean = false;
  public showLogin: boolean = false;

  showSignupModal() {
    this.showSignup = true;
  }
  successSignup() {
    this.showSignup = false;
  }
  cancelSignup() {
    this.showSignup = false;
  }
  showLoginModal() {
    this.showLogin = true;
  }
  successLogin() {
    this.showLogin = false;
  }
  cancelLogin() {
    this.showLogin = false;
  }
}
</script>


<style lang="scss">
@import "~bulma/css/bulma.css";
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
