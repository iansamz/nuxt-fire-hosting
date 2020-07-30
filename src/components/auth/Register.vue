<template>
  <div class="col-lg-6 col-md-12 the-container">
    <h3>Register</h3>
    <!-- <p>
      Your email address will not be shared. Required fields are
      marked
      <span
        style="color:red"
      >*</span>
    
    <form>
      <div class="row">
        <div class="col-md-12">
          <div class="form-group">
            <input
              class="form-control"
              name="name"
              id="name"
              placeholder="Name*"
              type="text"
              required
            />
          </div>
        </div>
        <div class="col-md-12">
          <div class="form-group">
            <input class="form-control" placeholder="Email*" type="email" required />
          </div>
        </div>
        <div class="col-md-12">
          <div class="form-group">
            <input class="form-control" placeholder="Password*" type="text" required />
          </div>
        </div>
        <div class="col-md-12">
          <div class="form-group">
            <input class="form-control" placeholder="Phone Number*" type="text" required />
          </div>
        </div>
      </div>
      <div class="clearfix">
        <button class="btn btn-primary" type="submit">Signup</button>
      </div>
    </form>-->

    <div class="socials">
      <div class="google">
        <div class="clearfix">
          <button class="btn btn-primary" @click="googleSignin">
            <img src="~assets/images/google.svg" alt="Google Sign in" />
            Register
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
// import { mapState, mapGetters } from "vuex";
import * as firebase from "firebase";

export default Vue.extend({
  // computed: {
  //   ...mapState({
  //     authUser: (state: any) => state.authUser
  //   }),
  //   ...mapGetters({
  //     isLoggedIn: "isLoggedIn"
  //   })
  // },
  data: () => ({
    // formData: {
    //   email: "",
    //   password: ""
    // },
    // formValid: false,
    // formRules: {
    //   email: [
    //     (v: string) => !!v || "E-mail is required",
    //     (v: string) => /.+@.+\..+/.test(v) || "E-mail must be valid"
    //   ],
    //   // names: [
    //   //   (v: string) => !!v || "Name is required",
    //   //   (v: string) =>
    //   //     (v && v.length <= 10) || "Name must be less than 10 characters"
    //   // ],
    //   password: [(v: string) => !!v || "E-mail is required"]
    // }
  }),
  methods: {
    async googleSignin() {
      const provider = new firebase.auth.GoogleAuthProvider();

      return this.$fireAuth.signInWithPopup(provider).then(res => {
        this.$router.replace("/");
      });
    }
    //   async createUser() {
    //     try {
    //       await this.$fireAuth.createUserWithEmailAndPassword(
    //         this.formData.email,
    //         this.formData.password
    //       );
    //     } catch (e) {
    //       alert(e);
    //     }
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