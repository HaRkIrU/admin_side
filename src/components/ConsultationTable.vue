<template>
  <v-data-table
    :search="search"
    :headers="headers"
    :items="displayedLogs"
    :sort-by="[{ key: 'studentId', order: 'asc' }]"
    
    
  >
    <template v-slot:top >
      <v-toolbar flat >
<<<<<<< HEAD

        <v-toolbar-title class="text-h6 font-weight-black " style="color: #2F3F64">Consultation Records</v-toolbar-title>

=======
        <v-toolbar-title class="text-h6 font-weight-black " style="color: #2F3F64">Daily Logs</v-toolbar-title>
>>>>>>> parent of 61f361d (updated_consultation-records)
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
      
<<<<<<< HEAD

        <v-dialog v-model="dialog" max-width="1000px" class="custom-dialog">
=======
        <v-dialog v-model="dialog" max-width="1000px">
>>>>>>> parent of 61f361d (updated_consultation-records)
          
          <template v-slot:activator="{ props }">
            <v-btn class="mb-2 rounded-l	" color="primary" dark v-bind="props" prepend-icon="mdi-plus">Add Log</v-btn>
          </template>
          
<<<<<<< HEAD
          <v-card>

=======
          <v-card >
>>>>>>> parent of 61f361d (updated_consultation-records)
            <v-card-title ><span class="text-h6 m-2" style="color: #2F3F64"  >{{ formTitle }}</span></v-card-title>
            <v-card-text > 
              <v-container >
                <v-row dense >
                  <v-col
                  cols="12"
                  md="3"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.student_lrn"
                    label="LRN*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="4"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.email"
                    label="Email Address*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                cols="12"
                md="4"
                sm="6"
                ></v-col>

<<<<<<< HEAD
          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.complaint" label="Diagnosis*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.blood_pressure" label="Blood Pressure*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.pulse_rate" label="Pulse Rate*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.oxygen_sat" label="Oxygen Sat*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.temp" label="Temperature*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.treatment" label="Medicine Given" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.time_in" label="Time In*" required></v-text-field>
          </v-col>

          <v-col cols="12" md="4" sm="6">
            <v-text-field v-model="editedItem.time_out" label="Time Out*" required></v-text-field>
          </v-col>

=======
                <v-col
                  cols="12"
                  md="3"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.first_name"
                    label="First Name*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
                  sm="4"
                >
                  <v-text-field
                    v-model="editedItem.middle_name"
                    hint="example of helper text only on focus"
                    label="Middle Name"
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
                  sm="4"
                >
                  <v-text-field
                    v-model="editedItem.last_name"
                    label="Last Name*"
                    persistent-hint
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="1"
                  sm="4"
                >
                  <v-text-field
                    v-model="editedItem.extension"
                    label="Extension Name*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="2"
                  sm="6"
                >
                  <v-select
                    v-model="editedItem.sex_at_birth"
                    :items="['Male', 'Female', 'Other']"
                    label="Sex*"
                    required
                  ></v-select>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.birth_date"
                    label="Birthdate*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.birth_place"
                    label="Birthplace*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="2"
                  sm="6"
                >
                  <v-select
                    v-model="editedItem.civil_status"
                    :items="['Single','Married','Divorced']"
                    label="Civil Status*"
                    required
                  ></v-select>
                </v-col>
                
                <v-col
                  cols="12"
                  md="2"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.citizenship"
                    label="Citizenship*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="2"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.religion"
                    label="Religion*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.street"
                    label="Street*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.barangay"
                    label="Barangay*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.city"
                    label="City*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.province"
                    label="Provice*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.region"
                    label="Region*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.zip_code"
                    label="Zip Code*"
                    required
                  ></v-text-field>
                </v-col>
>>>>>>> parent of 61f361d (updated_consultation-records)
                
          </v-row>
              </v-container>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue-darken-1" variant="text" @click="close">Cancel</v-btn>
              <v-btn color="blue-darken-1" variant="text" @click="save">Save</v-btn>
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
      <tr>
        <td>{{ item.student_id }}</td>
<<<<<<< HEAD
        <td>{{ item.complaint }}</td>
        <td>{{ item.medicine_id }}</td>
        <td>{{ item.blood_pressure }}</td>
        <td>{{ item.pulse_rate }}</td>
        <td>{{ item.oxygen_sat }}</td>
        <td>{{ item.temp }}</td>
        <td>{{ item.treatment }}</td>
=======
        <td>{{ item.diagnosis }}</td>
        <td>{{ item.prod_name }}</td>
        <td>{{ item.date }}</td>
>>>>>>> parent of 61f361d (updated_consultation-records)
        <td>{{ item.time_in }}</td>
        <td>{{ item.time_out }}</td>
          <!-- Edit
          <v-icon class="me-2" size="small" style="color: #2F3F64" @click="editItem(item)">mdi-pencil</v-icon>
<<<<<<< HEAD

=======
        -->
       
        <td>
>>>>>>> parent of 61f361d (updated_consultation-records)
          <v-icon size="small" style="color: #2F3F64" @click="deleteItem(item)">mdi-delete</v-icon>
        </td>
      </tr>
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
      { title: 'Student ID', align: 'start', key:'student_id'},
<<<<<<< HEAD
      { title: 'Diagnosis', key: 'diagnosis' },
<<<<<<< HEAD
      { title: 'BP', key: 'blood_pressure' },
      { title: 'PR', key: 'pulse_rate' },
      { title: 'Temp', key: 'temperature' },
=======
>>>>>>> parent of 61f361d (updated_consultation-records)
      { title: 'Medicine', key: 'prod_name' },  
      { title: 'Date', key: 'date' },
      { title: 'Time-In', key: 'time_in' },
      { title: 'Time-Out', key: 'time_out' },
<<<<<<< HEAD
=======
      { title: 'Diagnosis'},
      { title: 'Medicine' },  
      { title: 'Blood Pressure' }, 
      { title: 'Pulse Rate' },   
      { title: 'Oxygen Sat' },   
      { title: 'Temperature' },   
      { title: 'Treatment' },  
      { title: 'Time-In' },
      { title: 'Time-Out' },
>>>>>>> 99edf950ab6fe4be87f9776240f488e34a9f5ca2
      { title: 'Actions', sortable: false }, 
=======
      { title: 'Delete', sortable: false }, 
>>>>>>> parent of 61f361d (updated_consultation-records)
    ],
    logs: [],
    editedIndex: -1,
    editedItem: {
      complaint: '',
      medicine_id: '',
      student_id: '',
<<<<<<< HEAD
      treatment: '',
      blood_pressure: '',
      pulse_rate: '',
      oxygen_sat: '',
      temp: '',
=======
      diagnosis: '',
>>>>>>> parent of 61f361d (updated_consultation-records)
      prod_name: '',
      time_in: '',
      time_out: '',
      is_timeout: '',
    },
    defaultItem: {
      complaint: '',
      medicine_id: '',
      student_id: '',
<<<<<<< HEAD
      treatment: '',
      blood_pressure: '',
      pulse_rate: '',
      oxygen_sat: '',
      temp: '',
=======
      diagnosis: '',
>>>>>>> parent of 61f361d (updated_consultation-records)
      prod_name: '',
      time_in: '',
      time_out: '',
      is_timeout: '',
    },
    
  }),

  computed: {
    formTitle() {
      return this.editedIndex === -1 ? 'Add Log' : 'Edit Student Information';
    },
    displayedLogs() {
      const searchTerm = this.search.toLowerCase(); // Convert search input to lowercase for case-insensitive comparison
    return this.logs.filter(log =>
      Object.values(log).some(value =>
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
<<<<<<< HEAD

      axios.get('http://127.0.0.1:8000/api/consultation-records')
        .then(response => {
          // Handle successful response
          this.logs = response.data;
          console.log(response.data);
        })
        .catch((error) => {
          // Handle error
          console.error('There was an error!', error);
      });
=======
      this.log = [
        { 
      student_id: '202111003',
      diagnosis: 'Cancer',
      prod_name: 'Chemotherapy Pills',
      date: '12/21/03',
      time_in: '8:00am',
      time_out: '11:00am',
    },
    { 
      student_id: '202111004',
      diagnosis: 'Ligma',
      prod_name: 'Chemotherapy Pills',
      date: '12/22/03',
      time_in: '3:00am',
      time_out: '5:00am',
    },
    { 
      student_id: '202111005',
      diagnosis: 'Diabetes',
      prod_name: 'Chemotherapy Pills',
      date: '12/23/03',
      time_in: '1:00am',
      time_out: '2:00am',
    },
    { 
      student_id: '202111006',
      diagnosis: 'Diarrhea',
      prod_name: 'Chemotherapy Pills',
      date: '12/25/03',
      time_in: '7:00am',
      time_out: '8:00am',
    },
    { 
      student_id: '202111007',
      diagnosis: 'Aids',
      prod_name: 'Chemotherapy Pills',
      date: '12/24/03',
      time_in: '5:00am',
      time_out: '6:00am',
    },

      ];
>>>>>>> parent of 61f361d (updated_consultation-records)
  },

    editItem(item) {
      this.editedIndex = this.logs.indexOf(item);
      this.editedItem = Object.assign({}, item);
      this.dialog = true;
    },

    deleteItem(item) {
      this.editedIndex = this.logs.indexOf(item);
      this.editedItem = Object.assign({}, item);
      this.dialogDelete = true;
      this.id = item.id;
    },

    deleteItemConfirm() {
      this.logs.splice(this.editedIndex, 1);

        // axios
        // .delete("http://127.0.0.1:8000/api/consultation-records/" + this.id)
        // .then((response) => {
        //   this.initialize();
        // })
        // .catch((error) => {
        //   // Handle error
        //   console.error("There was an error!", error);
        // });


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
        console.log(this.editedItem);

        axios
          .put(
            "http://127.0.0.1:8000/api/consultation-records/" + this.editedItem.id,
            this.editedItem
          )
          .then((response) => {
            this.initialize();
          })
          .catch((error) => {
            // Handle error
            console.error("There was an error!", error);
          });


        Object.assign(this.logs[this.editedIndex], this.editedItem);
      } else {

        axios.post('http://127.0.0.1:8000/api/consultation-records', this.editedItem)
        .then(response => {
          this.initialize();
        }).catch(error => {
          // Handle error
          console.error('There was an error!', error);
        });

        this.logs.push(this.editedItem);
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
