<template>
  <v-data-table
    :search="search"
    :headers="headers"
    :items="displayedStudents"
    :sort-by="[{ key: 'studentId', order: 'asc' }]"
  >
    <template v-slot:top>
      <v-toolbar flat>
        <v-toolbar-title class="text-h6 font-weight-black" style="color: #2F3F64">Student Table</v-toolbar-title>
        
        <v-text-field
          v-model="search"
          class="w-auto mr-4"
          density="compact"
          label="Search"
          prepend-inner-icon="mdi-magnify"
          variant="solo-filled"
          flat
          hide-details
          single-line
        ></v-text-field>

        <v-dialog v-model="dialog" max-width="1000px">
          <v-card>
            <v-card-title class="d-flex justify-center">
              <span class="text-h6 m-2" style="color: #2F3F64">Medical History</span>
            </v-card-title>
            <v-card-text>
              <v-data-table
                :items="[editedItem]"
                item-key="email"
                hide-default-footer
              >
                <template v-slot:items="props">
                  <td>{{ props.item.date }}</td>
                  <td>{{ props.item.student_id }}</td>
                  <td>{{ props.item.diagnosis }}</td>
                  <td>{{ props.item.blood_pressure }}</td>
                  <td>{{ props.item.pulse_rate }}</td>
                  <td>{{ props.item.temperature }}</td>
                  <td>{{ props.item.medicine }}</td>
                  <td>{{ props.item.description }}</td>
                </template>
                <template v-slot:headers="props">
                  <tr>
                    <th>Date</th>
                    <th>Student ID</th>
                    <th>Diagnosis</th>
                    <th>Blood Pressure</th>
                    <th>Pulse Rate</th>
                    <th>Temperature</th>
                    <th>Medicine</th>
                    <th>Description</th>
                  </tr>
                </template>
              </v-data-table>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue-darken-1" variant="text" @click="close">Close</v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>

        <v-dialog v-model="dialogDelete" max-width="500px">
          <v-card>
            <v-card-title class="text-h5">Are you sure you want to delete this item?</v-card-title>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue-darken-1" variant="text" @click="closeDelete">Cancel</v-btn>
              <v-btn color="blue-darken-1" variant="text" @click="deleteItemConfirm">OK</v-btn>
              <v-spacer></v-spacer>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-toolbar>
    </template>

    <template v-slot:item="{ item }">
      <v-hover v-slot:default="{ isHovering }">
        <tr
          @click="editItem(item)"
          :class="['student-row', { 'hover-effect': isHovering }]"
          style="cursor: pointer;"
        >
          <td>{{ item.first_name }} {{ item.middle_name }} {{ item.last_name }} {{ item.extension }}</td>
          <td>{{ item.student_id }}</td>
          <td>{{ item.student_lrn }}</td>
          <td>{{ item.grade_level }}</td>
        </tr>
      </v-hover>
    </template>
  </v-data-table>
</template>

<script>

import axios from 'axios';

export default {
  data: () => ({
    search: '',
    dialog: false,
    dialogDelete: false,
    headers: [
      { title: 'Name', align: 'start', key: 'full_name' },
      { title: 'Student ID', key: 'student_id' },
      { title: 'LRN', key: 'student_lrn' },
      { title: 'Grade Level', key: 'grade_level' },
    ],
    students: [
      {
    first_name: 'John',
    middle_name: 'Doe',
    last_name: 'Smith',
    extension: '',
    grade_level: '10',
    student_lrn: '1234567890',
    student_id: '2021001',
  },
    ],
    editedIndex: -1,
    editedItem: {
      date: '', 
      diagnosis: '',
      blood_pressure: '',
      pulse_rate: '',
      temperature: '',
      medicine: '',
      description: ''
    },
    defaultItem: {
      date: '',
      diagnosis: '',
      blood_pressure: '',
      pulse_rate: '',
      temperature: '',
      medicine: '',
      description: ''
    },
  }),

  computed: {
    formTitle() {
      return this.editedIndex === -1 ? 'Add Student' : 'Edit Student Information';
    },  
  displayedStudents() {
    const searchTerm = this.search.toLowerCase();
    return this.students.filter((student) => {
      const fullName = `${student.first_name} ${student.middle_name} ${student.last_name} ${student.extension}`.toLowerCase();
      return Object.values(student).some(
        (value) =>
          typeof value === 'string' && value.toLowerCase().includes(searchTerm)
      ) || fullName.includes(searchTerm);
    });
  },
},
  watch: {
    dialog(val) {
      val || this.close();
    },
    dialogDelete(val) {
      val || this.closeDelete();
    },
  },

  created() {
    this.initialize();
  },

  methods: {
    initialize() {
<<<<<<< HEAD
  this.students = [
    {
      date: '12/23/25',
      student_id: '2021004',
      diagnosis: 'Flu',
      blood_pressure: '120/60',
      pulse_rate: '60 bpm',
      temperature: '37',
      medicine: 'Paracetamol',
      description: 'Early Dismissal',
=======

      axios.get('http://127.0.0.1:8888/api/student')
        .then(response => {
          // Handle successful response
        let all_students = response.data;
        var juniors = all_students.filter(function (el) {
          return el.grade_level <= 10;
        });

        this.students = juniors;
          console.log(response.data);
        })
        .catch(error => {
          // Handle error
          console.error('There was an error!', error);
      });

>>>>>>> 99edf950ab6fe4be87f9776240f488e34a9f5ca2
    },
    // Add more medical history entries here...
  ];
},
    editItem(item) {
      this.editedIndex = this.students.indexOf(item);
      this.editedItem = Object.assign({}, item);
      this.editedMedicalHistory = {
  };
      this.dialog = true;
    },
    deleteItem(item) {
      this.editedIndex = this.students.indexOf(item);
      this.dialogDelete = true;
    },
    deleteItemConfirm() {
      this.students.splice(this.editedIndex, 1);
      this.closeDelete();
    },
    close() {
      this.dialog = false;
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem);
        this.editedIndex = -1;
      });
    },
    closeDelete() {
      this.dialogDelete = false;
      this.$nextTick(() => {
        this.editedItem = Object.assign({}, this.defaultItem);
        this.editedIndex = -1;
      });
    },
    save() {
      if (this.editedIndex > -1) {
        Object.assign(this.students[this.editedIndex], this.editedItem);
      } else {
        this.students.push(this.editedItem);
      }
      this.close();
    },
  },
};
</script>

<style scoped>
.hover-effect {
  background-color: #f5f5f5;
}
.student-row:hover {
  background-color: #f5f5f5;
}
</style>
