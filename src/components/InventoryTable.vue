<template>
  <v-data-table
    :search="search"
    :headers="headers"
    :items="displayedProducts"
    :sort-by="[{ key: 'prod_id', order: 'asc' }]"
<<<<<<< HEAD
  >
    <template v-slot:top>
=======
    
    
  >
    <template v-slot:top >
>>>>>>> origin/main
      <v-toolbar flat >
        <v-toolbar-title class="text-h6 font-weight-black " style="color: #2F3F64">Inventory Table</v-toolbar-title>
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
      
        <v-dialog v-model="dialog" max-width="800px" max-height="400px">
          
          <template v-slot:activator="{ props }">
            <v-btn class="mb-2 rounded-l" color="primary" dark v-bind="props" prepend-icon="mdi-plus">Add Product / Medicine</v-btn>
          </template>
          
          <v-card class="border-s-lg dark" border-info>
            <v-card-title class="text-h4 mt-4" style="color: #2F3F64">{{ formTitle }}</v-card-title>
            <v-divider :thickness="2"></v-divider>
            <v-card-text > 
              <v-container >
                <v-row dense >
                  <v-col
                  cols="12"
                  md="3"
                  sm="6"
                >
                  <v-text-field
<<<<<<< HEAD
                    v-model="editedItem.medicine_name"
=======
                    v-model="editedItem.prod_name"
>>>>>>> origin/main
                    label="Product Name*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
                  sm="12"
                >
                  <v-text-field
<<<<<<< HEAD
                    v-model="editedItem.quantity"
=======
                    v-model="editedItem.prod_qty"
>>>>>>> origin/main
                    label="Quantity*"
                    required
                  ></v-text-field>
                </v-col>
<<<<<<< HEAD

                <v-col
                  cols="12"
                  md="3"
                  sm="12"
                >
                  <v-text-field
                    v-model="editedItem.unit"
                    label="Unit*"
=======
                
                <v-col
                cols="12"
                md="4"
                sm="6"
                ></v-col>

                <v-col
                  cols="12"
                  md="4"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.prod_added"
                    label="Date Added*"
                    required
                  ></v-text-field>
                </v-col>
                <!--
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
>>>>>>> origin/main
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col
                  cols="12"
                  md="3"
<<<<<<< HEAD
                  sm="12"
                >
                  <v-text-field
                    v-model="editedItem.size"
                    label="Size*"
                    required
                  ></v-text-field>
                </v-col>

                <v-col
                  cols="12"
                  md="4"
                  sm="6"
                >
                  <v-text-field
                    v-model="editedItem.expiration_date"
                    label="Expiration*"
                    required
                  ></v-text-field>
                </v-col>
        
=======
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
                 -->
>>>>>>> origin/main
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
<<<<<<< HEAD
        <td class="text-center">{{ item.medicine_id }}</td>
        <td class="text-center">{{ item.medicine_name }}</td>
        <td class="text-center">{{ item.unit }}</td>
        <td class="text-center">{{ item.size }}</td>
        <td class="text-center">{{ item.quantity }}</td>
        <td class="text-center">{{ item.expiration_date }}</td>
=======
        <td class="text-center">{{ item.prod_id }}</td>
        <td class="text-center">{{ item.prod_name }}</td>
        <td class="text-center">{{ item.prod_unit }}</td>
        <td class="text-center">{{ item.prod_size }}</td>
        <td class="text-center">{{ item.prod_qty }}</td>
        <td class="text-center">{{ item.prod_exp }}</td>
>>>>>>> origin/main
        <td class="text-center"> <v-icon class="me-2" size="small" style="color: #2F3F64" @click="editItem(item)">mdi-pencil </v-icon> <v-icon size="small" style="color: #2F3F64" @click="deleteItem(item)">mdi-delete </v-icon> </td>
         
      </tr>
    </template>
    <!-- <template v-slot:no-data>
      <v-btn class="text-h2" color="primary" @click="initialize">Reset</v-btn>
    </template> -->
  </v-data-table>
</template>

<script>
<<<<<<< HEAD
import axios from 'axios';
=======

>>>>>>> origin/main
export default {
  
  data: () => ({
    search: '',
    dialog: false,
    dialogDelete: false,
    headers: [
      { title: 'ID', align: 'center', key:'prod_id'},
      { title: 'Name', align: 'center', key: 'prod_name' },
      { title: 'Unit', align: 'center', key: 'prod_unit' },
      { title: 'Size', align: 'center', key: 'prod_size' },
      { title: 'Quantity', align: 'center', key: 'prod_qty' },
      { title: 'Expiration Date', align: 'center', key: 'prod_exp' },
      { title: 'Actions', align: 'center', sortable: false },
    ],
    product: [],
    editedIndex: -1,
    editedItem: {
<<<<<<< HEAD
      medicine_id: '',
      medicine_name: '',
      unit: '',
      size: '',
      quantity: '',
      expiration_date: '',
    },
    defaultItem: {
      medicine_id: '',
      medicine_name: '',
      unit: '',
      size: '',
      quantity: '',
      expiration_date: '',
=======
      prod_id: '',
      prod_name: '',
      prod_unit: '',
      prod_size: '',
      prod_qty: '',
      prod_exp: '',
    },
    defaultItem: {
      prod_id: '',
      prod_name: '',
      prod_unit: '',
      prod_size: '',
      prod_qty: '',
      prod_exp: '',
>>>>>>> origin/main
    },
    
  }),

  computed: {
    formTitle() {
      return this.editedIndex === -1 ? 'Add Product' : 'Edit Product Information';
    },
    displayedProducts() {
      const searchTerm = this.search.toLowerCase(); // Convert search input to lowercase for case-insensitive comparison
    return this.product.filter(product =>
      Object.values(product).some(value =>
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
      axios.get('http://127.0.0.1:8000/api/medicines')
        .then(response => {
          // Handle successful response
          this.product = response.data;
          console.log(response.data);
        })
        .catch(error => {
          // Handle error
          console.error('There was an error!', error);
      });
      this.product.forEach(product => {
          if (product.qty = 0) {
              // Remove the strand property
              product.qty = "Out of Stock";
          }
=======
      this.product = [
        { 
      prod_id: '1', 
      prod_name: 'Paracetamol', 
      prod_quantity: '1',
      prod_exp: 'December 25, 2024',
      prod_unit: 'Consumable',
      prod_size: 'Large'
    },
    { 
      prod_id: '2', 
      prod_name: 'Paracetamol', 
      prod_quantity: '0', 
    },
    { 
      prod_id: '3', 
      prod_name: 'Paracetamol', 
      prod_quantity: '0', 
    },
      ];
  
      this.product.forEach(product => {
    if (product.qty = 0) {
        // Remove the strand property
        product.qty = "Out of Stock";
    }
>>>>>>> origin/main
      });
    },

    editItem(item) {
<<<<<<< HEAD

      this.editedIndex = this.product.indexOf(item);
      this.editedItem = Object.assign({}, item);
      this.dialog = true;
      
=======
      this.editedIndex = this.product.indexOf(item);
      this.editedItem = Object.assign({}, item);
      this.dialog = true;
>>>>>>> origin/main
    },

    deleteItem(item) {
      this.editedIndex = this.product.indexOf(item);
<<<<<<< HEAD
      this.medicine_id = item.medicine_id;
=======
>>>>>>> origin/main
      this.editedItem = Object.assign({}, item);
      this.dialogDelete = true;
    },

    deleteItemConfirm() {
<<<<<<< HEAD
      
      this.product.splice(this.editedIndex, 1);
      

      axios.delete('http://127.0.0.1:8000/api/medicines/' + this.medicine_id)
        .then(response => {
          this.initialize();
        }).catch(error => {
          // Handle error
          console.error('There was an error!', error);
        });
        this.closeDelete();
=======
      this.product.splice(this.editedIndex, 1);
      this.closeDelete();
>>>>>>> origin/main
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
<<<<<<< HEAD

      if (this.editedIndex > -1) {
        axios.put('http://127.0.0.1:8000/api/medicines/' + this.editedItem.medicine_id, this.editedItem)
        .then(response => {

          this.initialize();

        }).catch(error => {
          // Handle error
          console.error('There was an error!', error);
        });

        Object.assign(this.product[this.editedIndex], this.editedItem);

      } else {

        axios.post('http://127.0.0.1:8000/api/medicines', this.editedItem)
        .then(response => {
          this.initialize();
        }).catch(error => {
          // Handle error
          console.error('There was an error!', error);
        });

=======
      if (this.editedIndex > -1) {
        Object.assign(this.product[this.editedIndex], this.editedItem);
      } else {
        this.product.push(this.editedItem);
>>>>>>> origin/main
      }
      this.close();
    },
    
  },
};
</script>
<style lang="scss">
.v-data-table {
  height: 100%;
  width: auto;
}
</style>
