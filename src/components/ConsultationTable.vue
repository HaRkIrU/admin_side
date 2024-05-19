<template>
  <v-data-table
    :search="search"
    :headers="headers"
    :items="displayedLogs"
    :sort-by="[{ key: 'studentId', order: 'asc' }]"
    
    
  >
    <template v-slot:top >
      <v-toolbar flat >
        <v-toolbar-title class="text-h6 font-weight-black " style="color: #2F3F64">Consultation Records</v-toolbar-title>
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
      
        <v-dialog v-model="dialog" max-width="1000px" class="custom-dialog">
          
          <template v-slot:activator="{ props }">
            <v-btn class="mb-2 rounded-l" color="primary" dark v-bind="props" prepend-icon="mdi-plus">Add Log</v-btn>
          </template>
          
          <v-card>
            <v-card-title ><span class="text-h6 m-2" style="color: #2F3F64"  >{{ formTitle }}</span></v-card-title>
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
        <td>{{ item.diagnosis }}</td>
        <td>{{ item.blood_pressure }}</td>
        <td>{{ item.pulse_rate }}</td>
        <td>{{ item.temperature }}</td>
        <td>{{ item.prod_name }}</td>
        <td>{{ item.date }}</td>
        <td>{{ item.time_in }}</td>
        <td>{{ item.time_out }}</td>
        <td>
          <v-icon class="me-2" size="small" style="color: #2F3F64" @click="editItem(item)">mdi-pencil</v-icon>
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

export default {
  
  data: () => ({
    search: '',
    dialog: false,
    dialogDelete: false,
    headers: [
      { title: 'Student ID', align: 'start', key:'student_id'},
      { title: 'Diagnosis', key: 'diagnosis' },
      { title: 'BP', key: 'blood_pressure' },
      { title: 'PL', key: 'pulse_rate' },
      { title: 'Temp', key: 'temperature' },
      { title: 'Medicine', key: 'prod_name' },  
      { title: 'Date', key: 'date' },
      { title: 'Time-In', key: 'time_in' },
      { title: 'Time-Out', key: 'time_out' },
      { title: 'Actions', sortable: false }, 
    ],
    log: [],
    editedIndex: -1,
    editedItem: {
      student_id: '',
      diagnosis: '',
      blood_pressure: '',
      pulse_rate: '',
      temperature: '',
      prod_name: '',
      date: '',
      time_in: '',
      time_out: '',
    },
    defaultItem: {
      student_id: '',
      diagnosis: '',
      blood_pressure: '',
      pulse_rate: '',
      temperature: '',
      prod_name: '',
      date: '',
      time_in: '',
      time_out: '',
    },
    
  }),

  computed: {
    formTitle() {
      return this.editedIndex === -1 ? 'Add Log' : 'Edit Student Information';
    },
    displayedLogs() {
      const searchTerm = this.search.toLowerCase(); // Convert search input to lowercase for case-insensitive comparison
    return this.log.filter(log =>
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
      this.log = [
        { 
      student_id: '202111003',
      diagnosis: 'Cancer',
      blood_pressure: '120/60',
      pulse_rate: '80',
      temperature: '36',
      prod_name: 'Chemotherapy Pills',
      date: '12/21/03',
      time_in: '8:00am',
      time_out: '11:00am',
      

    },
    { 
      student_id: '202111004',
      diagnosis: 'Ligma',
      blood_pressure: '120/60',
      pulse_rate: '80',
      temperature: '36',
      prod_name: 'Chemotherapy Pills',
      date: '12/22/03',
      time_in: '3:00am',
      time_out: '5:00am',
    },
    { 
      student_id: '202111005',
      diagnosis: 'Diabetes',
      blood_pressure: '120/60',
      pulse_rate: '80',
      temperature: '36',
      prod_name: 'Chemotherapy Pills',
      date: '12/23/03',
      time_in: '1:00am',
      time_out: '2:00am',
    },
    { 
      student_id: '202111006',
      diagnosis: 'Diarrhea',
      blood_pressure: '120/60',
      pulse_rate: '80',
      temperature: '36',
      prod_name: 'Chemotherapy Pills',
      date: '12/25/03',
      time_in: '7:00am',
      time_out: '8:00am',
    },
    { 
      student_id: '202111007',
      diagnosis: 'Aids',
      blood_pressure: '120/60',
      pulse_rate: '80',
      temperature: '36',
      prod_name: 'Chemotherapy Pills',
      date: '12/24/03',
      time_in: '5:00am',
      time_out: '6:00am',
    },

      ];
  },

    editItem(item) {
      this.editedIndex = this.log.indexOf(item);
      this.editedItem = Object.assign({}, item);
      this.dialog = true;
    },

    deleteItem(item) {
      this.editedIndex = this.log.indexOf(item);
      this.editedItem = Object.assign({}, item);
      this.dialogDelete = true;
    },

    deleteItemConfirm() {
      this.log.splice(this.editedIndex, 1);
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
