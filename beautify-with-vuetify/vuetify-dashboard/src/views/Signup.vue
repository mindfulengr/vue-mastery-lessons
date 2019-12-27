<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Singup</h1>
        <v-form>
          <v-text-field type="text" label="Email"></v-text-field>
          <v-autocomplete :items="browsers" label="Which browser do you use?"></v-autocomplete>
          <v-file-input label="Atach profile photo"></v-file-input>
          <v-text-field label="Birthday" v-model="birthday" readonly></v-text-field>
          <v-date-picker v-model="birthday"></v-date-picker>
          <v-checkbox label="Agree to terms & conditions"></v-checkbox>
          <v-btn type="submit" color="primary">Submit</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    birthday: "",
    browsers: ["Chrome", "Firefox", "Safari", "Edge", "Brave"]
  })
};
</script>

<style>
</style>