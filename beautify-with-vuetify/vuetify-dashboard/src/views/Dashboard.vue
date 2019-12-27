<template>
  <div>
    <h1>Dashboard</h1>
    <v-data-table
      :headers="headers"
      :items="employees"
      :items-per-page="5"
      class="elevation-1"
      @click:row="selectRow"
      multi-sort
    ></v-data-table>
    <v-snackbar v-model="snackbar">
      You have selected {{ currentItem.name }} the {{ currentItem.title }}
      <v-btn color="pink" text @click="snackbar = false">Close</v-btn>
    </v-snackbar>
  </div>
</template>
<script>
export default {
  data() {
    return {
      currentItem: {},
      snackbar: false,
      headers: [
        {
          text: "Employee ID",
          align: "left",
          sortable: false,
          value: "id"
        },
        { text: "Name", value: "name" },
        { text: "Title", value: "title" },
        { text: "Salary", value: "salary" }
      ],
      employees: [
        {
          id: 12875,
          name: "Dwight Schrute",
          title: "Assistant to the Regional Manager",
          salary: 65000
        },
        {
          id: 14094,
          name: "Kelly Kapoor",
          title: "Customer Service Representative",
          salary: 40000
        },
        {
          id: 12894,
          name: "Darryl Philbin",
          title: "Warehouse Foreman",
          salary: 68000
        },
        {
          id: 13893,
          name: "Angela Martin",
          title: "Accountant",
          salary: 54000
        },
        {
          id: 12943,
          name: "Phyllis Vance",
          title: "Saleswoman",
          salary: 65000
        },
        {
          id: 19523,
          name: "Karen Filippeli",
          title: "Saleswoman",
          salary: 65000
        },
        {
          id: 18349,
          name: "Toby Flenderson",
          title: "Human Resources Representative",
          salary: 60000
        },
        {
          id: 11853,
          name: "Michael Scott",
          title: "Regional Manager",
          salary: 70000
        },
        {
          id: 14821,
          name: "Pam Beasley",
          title: "Secretary",
          salary: 45000
        },
        {
          id: 15834,
          name: "Jim Halpert",
          title: "Salesman",
          salary: 65000
        }
      ]
    };
  },
  methods: {
    selectRow(event) {
      this.snackbar = true;
      this.currentItem = event;
    }
  }
};
</script>
