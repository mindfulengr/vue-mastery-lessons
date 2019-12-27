<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Singup</h1>
        <v-form ref="signUpForm">
          <v-text-field type="text" label="Email" :rules="emailRules"></v-text-field>
          <v-autocomplete :items="browsers" label="Which browser do you use?"></v-autocomplete>
          <v-file-input label="Atach profile photo"></v-file-input>
          <v-menu
            v-model="menu"
            :close-on-content-click="false"
            :nudge-right="40"
            transition="scale-transition"
            offset-y
            min-width="290px"
          >
            <template v-slot:activator="{ on }">
              <v-text-field v-model="birthday" label="Pick your birthday" readonly v-on="on"></v-text-field>
            </template>
            <v-date-picker v-model="birthday" @input="menu = false"></v-date-picker>
          </v-menu>
          <v-checkbox
            label="Agree to terms & conditions"
            v-model="agreeToTerms"
            :rules="agreeToTermsRules"
          ></v-checkbox>
          <v-btn class="mr-4" type="submit" color="primary">Submit</v-btn>
          <v-btn class="mr-4" @click="resetValidation" color="warning">Reset Validation</v-btn>
          <v-btn @click="resetForm" color="error">Reset Form</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    menu: false,
    agreeToTerms: false,
    agreeToTermsRules: [
      v =>
        !!v ||
        "You must agree to the terms and conditions to sign up for an account"
    ],
    emailRules: [
      v => !!v || "Email is required.",
      v => (v && v.includes("@")) || "Email should have an @ symbol",
      v =>
        (v && v.indexOf(".") - v.indexOf("@") > 1) ||
        "Email should contain a valid domain",
      v =>
        (v && v.indexOf(".") <= v.length - 3) ||
        "Email should have a valid domain extension"
    ],
    birthday: "",
    browsers: ["Chrome", "Firefox", "Safari", "Edge", "Brave"]
  }),
  methods: {
    resetValidation() {
      this.$refs.signUpForm.resetValidation();
    },
    resetForm() {
      this.$refs.signUpForm.reset();
    }
  }
};
</script>

<style>
</style>