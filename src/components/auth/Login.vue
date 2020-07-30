<template>
  <div class="col-lg-6 col-md-12 mrb-40 the-container">
    <h3>Login</h3>
    <!-- <p>
      Your email address will not be shared. Required fields are marked
      <span style="color:red">*</span>
    </p>
    <form @submit.prevent="submitForm">
      <div class="row">
        <div class="col-md-12">
          <div class="form-group">
            <input
              v-model="$v.formData.email.$model"
              class="form-control"
              v-bind:class="{ 'error': ($v.formData.email.$dirty && (!$v.formData.email.required || !$v.formData.email.email)) }"
              placeholder="Email*"
              type="email"
              required
            />
            <div
              class="error"
              v-if="$v.formData.email.$dirty && !$v.formData.email.required"
            >Email is required</div>
            <div
              class="error"
              v-if="$v.formData.email.$dirty && !$v.formData.email.email"
            >Email is invalid</div>
          </div>
          {{!$v.formData.email.$invalid }} {{ !$v.formData.password.$invalid }}
        </div>
        <div class="col-md-12">
          <div class="form-group">
            <input
              v-model.trim="$v.formData.password.$model"
              class="form-control"
              v-bind:class="{ 'error': ($v.formData.password.$dirty && (!$v.formData.password.required || !$v.formData.password.minLength)) }"
              placeholder="Password*"
              type="password"
              required
            />
            <div
              class="error"
              v-if="$v.formData.password.$dirty && !$v.formData.password.required"
            >Password is required</div>
            <div
              class="error"
              v-if="$v.formData.password.$dirty && !$v.formData.password.minLength"
            >Password must have at least {{$v.formData.password.$params.minLength.min}} characters.</div>
          </div>
        </div>
      </div>
      <div class="clearfix">
        <button
          class="btn btn-primary"
          type="submit"
          :disabled="$v.formData.email.$invalid && $v.formData.password.$invalid"
        >Login</button>
      </div>
    </form>-->
    <div class="socials">
      <div class="google">
        <div class="clearfix">
          <button class="btn btn-primary" @click="googleSignin">
            <img src="~assets/images/google.svg" alt="Google Sign in" />
            Login
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
// import { mapState, mapGetters } from "vuex";
// import { required, email, minLength } from "vuelidate/lib/validators";
import * as firebase from "firebase";

export default Vue.extend({
  computed: {
    // ...mapState({
    //   authUser: (state: any) => state.authUser
    // }),
    // ...mapGetters({
    //   isLoggedIn: "isLoggedIn"
    // })
  },
  data: () => ({
    // formData: {
    //   email: "",
    //   password: ""
    // },
    // formValid: false,
    // regEmail: /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,24}))$/,
    // error: {
    //   email: [] as string[],
    //   password: [] as string[],
    //   firebase: ""
    // }
  }),

  // validations: {
  //   formData: {
  //     email: {
  //       required,
  //       email
  //     },
  //     password: {
  //       required,
  //       minLength: minLength(6)
  //     }
  //   }
  // },
  methods: {
    async googleSignin() {
      const provider = new firebase.auth.GoogleAuthProvider();

      return this.$fireAuth.signInWithPopup(provider).then(res => {
        console.log(res);
        this.$router.replace("/");
      });
    }
    //   submitForm() {
    //     if (this.formData.email == null || this.formData.email == "") {
    //       this.error.email.push("Please Enter Email");
    //       return;
    //     } else if (!this.regEmail.test(this.formData.email)) {
    //       this.error.email.push("Please Enter Correct Email");
    //       return;
    //     }

    //     if (this.formData.password == null || this.formData.password == "") {
    //       this.error.password.push("Please Enter Password");
    //       return;
    //     }
    //     if (this.formData.password.length < 6) {
    //       this.error.password.push(
    //         "Password should be greater than 6 characters"
    //       );
    //       return;
    //     }

    //     return this.signInUser();
    //   },
    //   async signInUser() {
    //     try {
    //       await this.$fireAuth.signInWithEmailAndPassword(
    //         this.formData.email,
    //         this.formData.password
    //       );
    //     } catch (e) {
    //       alert(e);
    //     }
    //   }
  }
});
</script>

<style lang="scss" scoped>
.error {
  color: red;
  border-color: red;
}
.btn-primary {
  color: #f0582a !important;
  background-color: transparent;
  border-color: #f0582a;
  border: solid 2px !important;
  min-width: 250px;

  :hover {
    color: #000 !important;
    border-color: #000 !important;
    background-color: #f0582a;
    border: solid 2px !important;
  }

  img {
    width: 30px;
  }
}
.the-container {
  align-items: center;
  display: flex;
  justify-content: center;
  flex-direction: column;
}
</style>