<template>
  <v-data-table
    :search="search"
    :headers="headers"
    :items="displayedStudents"
    :sort-by="[{ key: 'studentId', order: 'asc' }]"
    
    
  >
    <template v-slot:top >
      <v-toolbar flat >
        <v-toolbar-title class="text-h6 font-weight-black " style="color: #2F3F64">Student Table</v-toolbar-title>
        <!-- <v-divider class="mx-2" inset vertical></v-divider> -->

        <v-text-field
        v-model="search"
        class="w-auto mr-4 "
        density="compact"
        label="Search"
        prepend-inner-icon="mdi-magnify"
        variant="solo-filled"
        flat
        hide-details
        single-line
      ></v-text-field>
      
        <v-dialog v-model="dialog" max-width="1000px">
<<<<<<< HEAD

=======
>>>>>>> parent of 61f361d (updated_consultation-records)
          
          <template v-slot:activator="{ props }">
            <v-btn class="mb-2 rounded-l	" color="primary" dark v-bind="props" prepend-icon="mdi-plus">Add Record</v-btn>
          </template>
<<<<<<< HEAD
<<<<<<< HEAD
        -->
          <v-card>
            <v-card-title class="d-flex justify-center">
              <span class="text-h6 m-2" style="color: #2F3F64">Medical History</span>
            </v-card-title>
=======
          

=======
          
>>>>>>> parent of 61f361d (updated_consultation-records)
          <v-card >
            <v-card-title ><span class="text-h6 m-2" style="color: #2F3F64"  >{{ formTitle }}</span></v-card-title>
>>>>>>> 99edf950ab6fe4be87f9776240f488e34a9f5ca2
            <v-card-text > 
              <v-container >
                <v-row dense >
                     <v-col cols="12" md="3" sm="6">
            <v-text-field v-model="editedItem.student_id" label="Student ID*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.diagnosis" label="Diagnosis*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.blood_pressure" label="Blood Pressure*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.pulse_rate" label="Pulse Rate*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.temperature" label="Temperature*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.prod_name" label="Product Name*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.date" label="Date*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.time_in" label="Time In*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.time_out" label="Time Out*" required></v-text-field>
          </v-col>
                
          </v-row>
              </v-container>
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
<<<<<<< HEAD
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
          <td>{{ item.strand }}</td>
        </tr>
      </v-hover>
=======
      <tr>
        <td>{{ item.first_name }} {{ item.middle_name }} {{ item.last_name }} {{ item.extension }}</td>
        <td>{{ item.student_id }}</td>
        <td>{{ item.student_lrn }}</td>
        <td>{{ item.grade_level }}</td>
        <td>{{ item.strand }}</td>
<<<<<<< HEAD

=======
>>>>>>> parent of 61f361d (updated_consultation-records)
        <td>
          <v-icon class="me-2" size="small" style="color: #2F3F64" @click="editItem(item)">mdi-pencil</v-icon>
          <v-icon size="small" style="color: #2F3F64" @click="deleteItem(item)">mdi-delete</v-icon>
        </td>
<<<<<<< HEAD

=======
>>>>>>> parent of 61f361d (updated_consultation-records)
      </tr>
>>>>>>> 99edf950ab6fe4be87f9776240f488e34a9f5ca2
    </template>
    <!-- <template v-slot:no-data>
      <v-btn class="text-h2" color="primary" @click="initialize">Reset</v-btn>
    </template> -->
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
      { title: 'Name', align: 'start', key:'full_name'},
      { title: 'Student ID', key: 'student_id' },
      { title: 'LRN', key: 'student_lrn' },
      { title: 'Grade Level', key: 'grade_level' },
      { title: 'Strand', key: 'strand' },
      { title: 'Actions', sortable: false },
    ],
    students: [],
    editedIndex: -1,
    editedItem: {
      student_id: '',
      student_lrn: '',
      grade_level: '',
      strand: '',
      first_name: '',
      middle_name: '',
      last_name: '',
      extension: '',
    },
    defaultItem: {
      student_id: '',
      student_lrn: '',
      grade_level: '',
      strand: '',
      first_name: '',
      middle_name: '',
      last_name: '',
      extension: '',
    },
    
  }),

  computed: {
    formTitle() {
      return this.editedIndex === -1 ? 'Add Student' : 'Edit Student Information';
    },
    displayedStudents() {
      const searchTerm = this.search.toLowerCase(); // Convert search input to lowercase for case-insensitive comparison
    return this.students.filter(student =>
      Object.values(student).some(value =>
        typeof value === 'string' && value.toLowerCase().includes(searchTerm)
    )
    );
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


      axios.get('http://127.0.0.1:8888/api/student')
        .then(response => {
          // Handle successful response
        let all_students = response.data;
        var seniors = all_students.filter(function (el) {
          return el.grade_level > 10;
        });

        this.students = seniors;
        console.log(response.data);
        })
        .catch(error => {
          // Handle error
          console.error('There was an error!', error);
    });
  

      this.students.forEach(student => {
  student.full_name = `${student.first_name} ${student.middle_name} ${student.last_name} ${student.extension}`.trim();
    if (student.grade_level < 11 || student.grade_level > 12) {
        // Remove the strand property
        student.strand = "N/A";
    }
      });
    },

    editItem(item) {
      this.editedIndex = this.students.indexOf(item);
      this.editedItem = Object.assign({}, item);
      this.dialog = true;
    },

    deleteItem(item) {
      this.editedIndex = this.students.indexOf(item);
      this.editedItem = Object.assign({}, item);
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

<style lang="scss">
.v-data-table {
  height: 100%;

}
</style>
