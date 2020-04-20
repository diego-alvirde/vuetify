<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Signup</h1>
        <v-form ref="signUpForm" v-model="formValidity">
          <v-text-field
            name="email"
            label="Email"
            id="email"
            v-model="email"
            :rules="emailRules"
            required
          ></v-text-field>
          <v-autocomplete label="Wich browser do you use?" :items="browsers">
          </v-autocomplete>
          <v-file-input label="Attach profile picture"> </v-file-input>
          <v-text-field
            label="Birthday"
            v-model="birthday"
            readonly
          ></v-text-field>
          <v-date-picker v-model="birthday"></v-date-picker>
          <v-checkbox
            v-model="agreeToTerms"
            :rules="agreeToTermsRules"
            label="Agree to terms & conditions"
          ></v-checkbox>
          <v-btn
            class="mr-4"
            color="primary"
            type="submit"
            :disabled="!formValidity"
            >Submit</v-btn
          >
          <v-btn
            class="mr-4"
            color="warning"
            type="submit"
            @click="resetValidation"
            >Reset Validation</v-btn
          >
          <v-btn class="mr-4" color="success" @click="validateForm"
            >Validate Form</v-btn
          >
          <v-btn color="error" type="submit" @click="resetForm">Reset</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      agreeToTerms: false,
      agreeToTermsRules: [(value) => !!value || "You must agree"],
      emailRules: [(value) => !!value || "Email is required"],
      birthday: "",
      browsers: ["Chrome", "Firefox", "Safari", "Edge"],
      formValidity: false,
    };
  },
  methods: {
    resetForm() {
      this.$refs.signUpForm.reset();
    },
    resetValidation() {
      this.$refs.signUpForm.resetValidation();
    },
    validateForm() {
      this.$refs.signUpForm.validate();
    },
  },
};
</script>
