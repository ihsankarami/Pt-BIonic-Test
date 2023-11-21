<template>
  <v-container class="fill-height">
    <v-responsive class="align-center fill-height bg-teal-lighten-4">
      <v-col class="bg-teal-lighten-4">
        <h1>Job requirement</h1>

        <h2>Job description</h2>
        <v-list class="bg-teal-lighten-4">
          <v-list-item v-for="(item, index) in jobReq.slice(0, 4)" :key="index">
            <li>{{ item.todo }}</li>
          </v-list-item>
        </v-list>

        <h2>Skills</h2>
        <v-list class="bg-teal-lighten-4">
          <v-list-item
            v-for="(item, index) in jobReq.slice(0, 4)"
            :key="index"
            class="bg-teal-lighten-4"
          >
            <li>{{ item.todo }}</li>
          </v-list-item>
        </v-list>
      </v-col>
      <v-col class="bg-teal-lighten-4">
        <h2>Skills</h2>
        <v-row>
          <v-col cols="12" sm="6">
            <div>Your name</div>
            <v-text-field label="Enter yor name" variant="underlined" flat>
            </v-text-field>
          </v-col>

          <v-col cols="12" sm="6">
            <div>Mobile number</div>
            <v-text-field
              label="Enter your mobile number"
              variant="underlined"
            ></v-text-field>
          </v-col>

          <v-col cols="12" sm="6" class="bg-teal-lighten-4">
            <div>Email Address</div>
            <v-text-field
              label="Enter your email "
              variant="underlined"
            ></v-text-field>
          </v-col>

          <v-col cols="12" sm="6">
            <div>Write your message here..</div>
            <v-text-field
              label="EWrite your message "
              variant="underlined"
            ></v-text-field>
          </v-col>
        </v-row>
      </v-col>
    </v-responsive>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      jobReq: "",
    };
  },
  mounted() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      fetch("https://dummyjson.com/todos/", {
        method: "GET",
      })
        .then((response) => {
          response.json().then((data) => {
            const filteredData = data.todos.filter((entry) => entry.id < 6);
            this.jobReq = filteredData;
          });
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
  onMounted() {},
};
</script>
