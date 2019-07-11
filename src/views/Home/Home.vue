<template>
  <div>
    <div>
      <b-navbar id="navbar" class="pl-sm-5 pr-sm-5" toggleable="lg" variant="faded" type="light">
        <b-navbar-brand href="#">
          <img :src="navBarBrand" width="35" height="35" alt="Kitten" />
        </b-navbar-brand>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav class="ml-auto text-center">
            <b-navbar-nav>
              <b-nav-item>
                <b-button pill size="sm" class="font-weight-light" v-b-modal.modal-signin>SIGN IN</b-button>
              </b-nav-item>
              <b-nav-item>
                <b-button
                  pill
                  size="sm"
                  class="font-weight-light"
                  v-b-modal.modal-create-account
                >REGISTER KIT</b-button>
              </b-nav-item>
            </b-navbar-nav>

            <b-nav-item-dropdown right>
              <!-- Using 'button-content' slot -->
              <template slot="button-content">
                <em>Help</em>
              </template>
              <b-dropdown-item v-if="path !== '/'" href="#">Profile</b-dropdown-item>
              <b-dropdown-item v-if="path !== '/'" href="#">Sign Out</b-dropdown-item>
              <b-dropdown-item v-if="path === '/'" href="#">About</b-dropdown-item>
            </b-nav-item-dropdown>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div>
    <div class="container">
      <img :src="collage" width="100%" alt="collage" />
      <div class="centered d-none d-md-block d-lg-none d-lg-block d-xl-none d-xl-block">
        <h1>MEET YOUR GENES</h1>
        <h5
          class="text-capitalize"
        >commit to a healthier you, inspired by your genes - with 125+ genetic reports.</h5>
        <b-button pill size="lg" class="mt-2 font-weight-lg-light" variant="danger">shop now</b-button>
      </div>
    </div>
    <div class="fixed-bottom">
      <div class="fluid-container footer">
        <p class="text-center pt-4 font-weight-lighter">&copy; 2019, WebDevCli. All Rights Reserved.</p>
      </div>
    </div>
    <!------------- 
      ** modal 
    --------------->
    <b-modal id="modal-signin" ref="modal" title="Sign in" no-close-on-backdrop hide-footer>
      <b-form @submit="onSubmit">
        <b-form-group id="input-group-1">
          <b-form-input id="input-1" v-model="form.email" type="email" required placeholder="Email"></b-form-input>
        </b-form-group>

        <b-form-group id="input-group-2">
          <b-form-input
            id="input-2"
            v-model="form.password"
            type="password"
            required
            placeholder="Password"
          ></b-form-input>
        </b-form-group>
        <p class="font-weight-bold">
          <a href="#">Forgot your password?</a>
        </p>
        <div class="text-center">
          <b-button type="submit" class="w-50" pill variant="primary">Sign in</b-button>
        </div>
      </b-form>
    </b-modal>
    <!-- modal 02 -->
    <b-modal id="modal-create-account" title="Create an account" no-close-on-backdrop hide-footer>
      <b-form @submit="onSubmit">
        <b-form-group id="input-group-3">
          <b-form-input id="input-3" v-model="form.fname" required placeholder="First name"></b-form-input>
        </b-form-group>
        <b-form-group id="input-group-4">
          <b-form-input id="input-4" v-model="form.lname" required placeholder="Last name"></b-form-input>
        </b-form-group>
        <b-form-group id="input-group-1">
          <b-form-input id="input-1" v-model="form.email" type="email" required placeholder="Email"></b-form-input>
        </b-form-group>

        <b-form-group id="input-group-2">
          <b-form-input
            id="input-2"
            v-model="form.password"
            type="password"
            required
            placeholder="Create password"
          ></b-form-input>
        </b-form-group>
        <b-form-group id="input-group-5">
          <b-form-input
            id="input-5"
            v-model="form.confirmpass"
            type="password"
            required
            placeholder="Confirm password"
          ></b-form-input>
        </b-form-group>
        <b-form-group id="input-group-7">
          <b-form-input id="input-7" v-model="form.date" type="date" required></b-form-input>
        </b-form-group>
        <b-form-group id="input-group-6">
          <b-form-checkbox-group v-model="form.checked" id="checkboxes-6">
            <b-form-checkbox value="me">
              I have read and agree to the
              <a href="#">Terms of service</a> and
              <a href="#">Privacy Statement</a>
            </b-form-checkbox>
          </b-form-checkbox-group>
        </b-form-group>

        <div class="text-center">
          <b-button type="submit" class="w-50" pill variant="primary">create account</b-button>
        </div>
      </b-form>
    </b-modal>
  </div>
</template>

<script>
// @ is an alias to /src
import navBarBrand from "@/assets/group.svg";
import collage from "@/assets/people/collage.jpg";
export default {
  name: "home",
  data() {
    return {
      navBarBrand: navBarBrand,
      collage: collage,
      path: this.$route.fullPath,
      form: {
        email: "",
        password: "",
        confirmpass: "",
        fname: "",
        lname: "",
        date: "",
        checked: []
      }
    };
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault();
      alert(JSON.stringify(this.form));
    }
  }
};
</script>
<style scoped>
#navbar {
  /* border-bottom: 1px lightgray; */
  /* box-shadow: 0px 2px 7px 1px #888888; */
}
.container {
  position: relative;
  text-align: center;
  color: white;
}
.centered {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.fluid-container.footer {
  background: lightgrey;
  height: 70px;
}
.fluid-container.footer > *:last-child {
  margin-bottom: 0px;
  color: black;
}
</style>

