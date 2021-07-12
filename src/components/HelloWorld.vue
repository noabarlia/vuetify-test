<template>
  <v-container>
    <v-row no-gutters justify="center" class="mt-3">
      <v-col md="4">
        <v-text-field
          v-model="value"
          label="הוסף משימה"
          filled
          outlined
          dense
          @input="update"
        ></v-text-field>
      </v-col>
      <v-btn
        name="append"
        rounded
        color="primary"
        dark
        class="mr-3"
        @click="addTask"
      >
        הוסף
      </v-btn>
    </v-row>

    <v-divider></v-divider>
    <v-row no-gutters justify="center">
      <v-col md="8">
        <div>
          <v-subheader>משימות</v-subheader>
          <v-simple-table class="grey lighten-5">
            <tbody>
              <tr v-for="task in tasks" :key="task">
                <td width="99%">
                  <span>{{ task.description }}</span>
                </td>
                <td>
                  <v-btn icon color="grey">
                    <v-icon @click="removeTask(task.id)"
                      >mdi-delete-circle-outline</v-icon
                    >
                  </v-btn>
                </td>
              </tr>
            </tbody>
          </v-simple-table>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>


<script>
export default {
  name: "HelloWorld",

  data: () => ({
    tasks: [{ id: 0, description: "ללכת לקניות" }],
    counter: 0,
    description: "",
  }),

  methods: {
    update(value) {
      this.description = value;
      console.log(this.description);
    },

    addTask() {
      this.tasks.push({ id: ++this.counter, description: this.description });
    },

    removeTask(id) {
      console.log(id);
      this.tasks.splice(id, 1);
    },
  },
};
</script>
