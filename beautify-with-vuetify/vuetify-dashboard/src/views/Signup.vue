<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Singup</h1>
        <v-form>
          <v-text-field type="text" label="Email"></v-text-field>
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
    menu: false,
    birthday: "",
    browsers: ["Chrome", "Firefox", "Safari", "Edge", "Brave"]
  })
};
</script>

<style>
</style>