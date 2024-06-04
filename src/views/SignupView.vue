<template>
  <div class="container my-5">
    <div class="row justify-content-center">
      <div class="col-lg-6 col-8">
        <h1 class="my-5">This is Sign up page</h1>

        <div class="row">
          <label for="username">Username</label>
          <input
            class="form-control"
            type="text"
            maxlength="8"
            v-model.trim="username"
            @input="checkUsername"
            ref="usernameInput"
          />
          <p v-if="errorMsg.username">{{ errorMsg.username }}</p>
        </div>
        <div class="row">
          <label for="email">Email</label>
          <input
            class="form-control"
            type="email"
            v-model.trim="email"
            @input="checkEmail"
            ref="emailInput"
          />
          <p v-if="errorMsg.email" class="text-danger">{{ errorMsg.email }}</p>
        </div>
        <div class="row">
          <label for="password">Password</label>
          <input
            class="form-control"
            type="password"
            minlength="6"
            v-model.trim="password"
            @input="checkPassword"
            ref="passwordInput"
          />
          <p v-if="errorMsg.password" class="text-danger">
            {{ errorMsg.password }}
          </p>
        </div>
        <div class="row">
          <label for="confirmPassword">Confirm password</label>
          <input
            class="form-control"
            type="password"
            minlength="6"
            v-model.trim="confirmPassword"
            @input="checkCPassword"
            ref="confirmPasswordInput"
          />
          <p v-if="errorMsg.confirmPassword" class="text-danger">
            {{ errorMsg.confirmPassword }}
          </p>
        </div>
        <div class="my-4">
          <MDBBtn
            color="dark"
            v-bind:disabled="!formIsFilled"
            :class="['btn', submitButtonColor]"
            @click="signUp"
          >
            Sign up
          </MDBBtn>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "SignupView",
  data() {
    return {
      username: "",
      email: "",
      password: "",
      confirmPassword: "",
      errorMsg: [],
      canSubmit: false,
    };
  },
  computed: {
    formIsFilled: function () {
      return (
        this.username && this.email && this.password && this.confirmPassword
      );
    },
    submitButtonColor: function () {
      this.checkSubmit();
      if (this.formIsFilled && this.canSubmit) {
        return "btn-primary";
      } else {
        return "btn-outline-secondary";
      }
    },
  },
  methods: {
    checkUsername: function () {
      const input = this.$refs.usernameInput;

      if (!input.checkValidity()) {
        this.errorMsg.username = input.validationMessage;
      } else {
        this.errorMsg.username = null;
      }
    },
    checkEmail: function () {
      const input = this.$refs.emailInput;
      if (!input.checkValidity()) {
        this.errorMsg.email = input.validationMessage;
      } else {
        this.errorMsg.email = null;
      }
    },
    checkPassword: function () {
      const input = this.$refs.passwordInput;

      if (!/[\$\%\^\&\*]+/.test(this.password)) {
        this.errorMsg.password =
          "Username must include at least one special character: $, %, ^, &, or *";
      } else if (!input.checkValidity()) {
        this.errorMsg.password = input.validationMessage;
      } else {
        this.errorMsg.password = null;
      }
    },
    checkCPassword: function () {
      if (this.confirmPassword !== this.password) {
        this.errorMsg.confirmPassword = "Passwords do not match";
      } else {
        this.errorMsg.confirmPassword = null;
      }
    },
    checkSubmit: function () {
      this.canSubmit = true;

      for (let key in this.errorMsg) {
        if (this.errorMsg[key]) {
          this.canSubmit = false;
          break;
        }
      }
    },
  },
};
</script>
