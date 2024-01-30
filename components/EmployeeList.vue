<!-- <template>
    <div>
      <UCard>
        <div class="header">
          <UButton color="gray" @click="openDetailsModal('add')">Add</UButton>
        </div>
  
        <UModal v-model="isDetailsModalVisible">
          <UCard>
            <form v-if="currentOperation !== 'delete'" @submit.prevent="handleDetailsOperation">
              <p>Name: <input type="text" v-model="formData.name" /></p>
              <p>Age: <input type="number" v-model="formData.age" /></p>
              <p>
                Gender:
                <select v-model="formData.gender">
                  <option value="Male">Male</option>
                  <option value="Female">Female</option>
                </select>
              </p>
              <div class="flex">
                <UButton color="gray" type="submit">
                  {{ currentOperation === 'delete' ? 'Delete' : 'update' }}
                </UButton>
                <UButton color="gray" @click="closeDetailsModal">Close</UButton>
              </div>
            </form>
          </UCard>
        </UModal>
  
        <table class="details-table">
          <thead>
            <tr>
              <th>Name</th>
              <th>Age</th>
              <th>Gender</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item, index) of details" :key="index">
              <td>{{ item.name }}</td>
              <td>{{ item.age }}</td>
              <td>{{ item.gender }}</td>
              <td>
                <UButton color="gray" @click="openDetailsModal('edit', index)">Edit</UButton>
                <UButton color="gray" @click="openDetailsModal('delete', index)">Delete</UButton>
              </td>
            </tr>
          </tbody>
        </table>
        
      </UCard>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {
      const isDetailsModalVisible = ref(false);
      const formData = ref({ name: '', age: 0, gender: '' });
      const details = ref([]);
      let currentOperation = null;
      let currentOperationIndex = null;
  
      const openDetailsModal = (operation, index = null) => {
        currentOperation = operation;
        currentOperationIndex = index;
  
        if (operation === 'add') {
          formData.value = { name: '', age: 0, gender: '' };
        } else if (operation === 'edit' && index !== null) {
          formData.value = { ...details.value[index] };
        }
  
        isDetailsModalVisible.value = true;
      };
  
      const handleDetailsOperation = () => {
        if (currentOperation === 'add') {
          details.value.push({ ...formData.value });
        } else if (currentOperation === 'edit' && currentOperationIndex !== null) {
          details.value[currentOperationIndex] = { ...formData.value };
        } else if (currentOperation === 'delete' && currentOperationIndex !== null) {
          details.value.splice(currentOperationIndex, 1);
        }
  
        closeDetailsModal();
      };
  
      const closeDetailsModal = () => {
        isDetailsModalVisible.value = false;
        currentOperation = null;
        currentOperationIndex = null;
      };
  
      return { isDetailsModalVisible, formData, details, openDetailsModal, handleDetailsOperation, closeDetailsModal };
    },
  };
  </script>
  
  <style scoped>
  .details-table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
  }
  
  .details-table th, .details-table td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
  }
  
  .details-table th {
    background-color: #f2f2f2;
  }
  
  .details-table td {
    background-color: #fff;
  }
  
  .details-table button {
    margin-right: 5px;
  }
  </style> -->
  
  
<template>
    <div :key="render">
        <UCard>
            <div class="head">
                <UButton color="gray" @click="openDetails('add')">Add Details</UButton>
            </div>

            <UModal v-model="isModalVisible">
                <UCard>
                    <form v-if="currentOperation !== 'delete'" class="form-container">
                        <div>
                            <label for="name">Name:</label>
                            <input type="text" id="name" v-model="formData.name" />
                        </div>
                        <div>
                            <label for="age">Age:</label>
                            <input type="number" id="age" v-model="formData.age" />
                        </div>
                        <div>
                        <label for="gender">Gender:</label>
                        <select id="gender" v-model="formData.gender">
                            <option value="Male">Male </option>
                            <option value="Female">Female </option>
                        </select>
                    </div>




    <div v-if="formData.gender == 'Male'">
        <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="100" height="100" viewBox="0 0 128 128">
            <path
                d="M 56 21.900391 C 43.3 21.900391 33 32.200391 33 44.900391 C 33 46.600391 34.3 47.900391 36 47.900391 L 41.199219 47.900391 L 41.400391 47.900391 C 52.900391 47.900391 64.6 47.900391 73 40.400391 L 73 40.5 C 73.4 40.1 73.799609 39.800391 74.099609 39.400391 C 75.199609 38.200391 77.100781 37.999609 78.300781 39.099609 C 79.600781 40.199609 79.7 42.2 78.5 43.5 L 77.099609 44.900391 C 75.799609 46.200391 76.3 48.399609 78 49.099609 C 79 49.499609 80.099219 49.700781 81.199219 49.800781 C 82.699219 50.000781 83.900391 51.200781 83.900391 52.800781 L 83.900391 59.599609 C 84.000391 70.099609 76.000391 79.2 65.400391 80 C 53.800391 80.8 44.1 71.599609 44 60.099609 C 44 58.499609 42.799219 57.1 41.199219 57 C 39.499219 56.9 38 58.3 38 60 C 38 74.3 49.7 86 64 86 C 77.9 86 89.3 75.100781 90 61.300781 L 90 61 L 90 47 L 90 44 L 90 43 C 90 35.8 84.599609 29.899609 77.599609 29.099609 L 77.199219 28.5 C 74.299219 24.4 69.5 21.900391 64.5 21.900391 L 56 21.900391 z M 64 91 C 47.6 91 32.400781 99.899609 24.300781 114.09961 C 23.500781 115.49961 24.000391 117.39922 25.400391 118.19922 C 25.900391 118.49922 26.400391 118.59961 26.900391 118.59961 C 27.900391 118.59961 29 118.09961 29.5 117.09961 C 36.6 104.69961 49.8 97 64 97 C 78.2 97 91.4 104.69961 98.5 117.09961 C 99.3 118.49961 101.19961 118.99922 102.59961 118.19922 C 103.99961 117.39922 104.49922 115.49961 103.69922 114.09961 C 95.599219 99.899609 80.4 91 64 91 z">
            </path>
        </svg>
    </div>
    <div v-else-if="formData.gender == 'Female'">
        <svg xmlns="http://www.w3.org/2000/svg" x="0px" y="0px" width="100" height="100" viewBox="0 0 128 128">
            <path
                d="M 64 13 C 47.5 13 34 26.5 34 43 C 34 48.3 35.399609 53.499609 38.099609 58.099609 C 38.099609 58.699609 38 59.4 38 60 C 38 74.3 49.7 86 64 86 C 72.8 86 80.499219 81.6 85.199219 75 C 93.399219 74.9 100 68.2 100 60 C 100 58.2 99.699609 56.500391 99.099609 54.900391 C 102.69961 52.200391 105 47.9 105 43 C 105 34.7 98.3 28 90 28 C 84.8 19 75.1 13 64 13 z M 82.023438 42.603516 C 82.677344 42.624609 83.337891 42.850781 83.900391 43.300781 C 85.100391 44.200781 85.3 45.899219 84.5 47.199219 C 83.9 48.199219 83.299609 49.099609 82.599609 50.099609 C 82.199609 50.699609 82.000781 51.399609 82.300781 52.099609 C 83.500781 54.799609 84.100391 57.899609 83.900391 61.099609 C 83.400391 71.299609 75.000391 79.5 64.900391 80 C 53.500391 80.5 44 71.3 44 60 C 44 58.9 44.9 58.099609 46 58.099609 L 53.099609 58.099609 C 56.199609 58.099609 59.500781 57.699219 62.800781 56.699219 C 69.400781 54.699219 74.799609 50.7 78.099609 46 C 78.499609 45.4 78.900781 44.799609 79.300781 44.099609 C 79.863281 43.099609 80.933594 42.568359 82.023438 42.603516 z M 64 91 C 47.6 91 32.400781 99.899609 24.300781 114.09961 C 23.500781 115.49961 24.000391 117.39922 25.400391 118.19922 C 26.800391 118.99922 28.7 118.49961 29.5 117.09961 C 36.6 104.69961 49.8 97 64 97 C 78.2 97 91.4 104.69961 98.5 117.09961 C 99.1 118.09961 100.09961 118.59961 101.09961 118.59961 C 101.59961 118.59961 102.09961 118.49922 102.59961 118.19922 C 103.99961 117.39922 104.49922 115.49961 103.69922 114.09961 C 95.599219 99.899609 80.4 91 64 91 z">
            </path>
        </svg>
    </div>
    </form>


    <div v-if="currentOperation === 'delete'" class="delete-container">
        <p>Do you want to delete all details?</p>
        <div class="flex justify-center">
            <UButton color="gray" @click="formDelete">Yes</UButton>
            <UButton color="gray" @click="Deletion">No</UButton>
        </div>
    </div>

    <div v-else class="flex justify-center">
        <UButton color="gray" @click="thisOperation">
            {{ currentOperation === 'edit' ? 'Update' : 'Save' }}
        </UButton>
        <UButton color="gray" @click="closeModal">Close</UButton>
    </div>
    </UCard>
    </UModal>

    <table class="details-table">
        <thead>
            <tr>
                <th>Name</th>
                <th>Age</th>
                <th>Gender</th>
                <th>Actions</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(item, index) of details" :key="index">
                <td>{{ item.name }}</td>
                <td>{{ item.age }}</td>
                <td>{{ item.gender }}</td>
                <td>
                    <UButton color="gray" @click="openDetails('edit', index)">Edit</UButton>
                    <UButton color="gray" @click="openDetails('delete', index)">Delete</UButton>
                </td>
            </tr>
        </tbody>
    </table>

    </UCard>
</div></template>
  
<script setup>

const isModalVisible = ref(false)
const confirmDeleteModal = ref(false)
const formData = ref({ name: '', age: 0, gender: '' })
const details = ref([])
const currentOperation = ref()
const currentOperationIndex = ref()
const render = ref(0)
onMounted(()=>{
    details.value=JSON.parse(localStorage.getItem('detailsData'))||[]
})

function openDetails(operation, index = null) {
    currentOperation.value = operation;
    currentOperationIndex.value = index;

    if (operation === 'add') {
        formData.value = { name: '', age: 0, gender: '' };
    } else if (operation === 'edit' && index !== null) {
        formData.value = { ...details.value[index] };
    }

    isModalVisible.value = true;

}

function thisOperation() {
   

    if (currentOperation.value === 'add') {
        details.value.push({ ...formData.value });
    } else if (currentOperation.value === 'edit' && currentOperationIndex.value !== null) {
        details.value[currentOperationIndex.value] = { ...formData.value };
    }
localStorage.setItem('detailsData',JSON.stringify(details.value))
    closeModal();
}

function formDelete() {
    details.value.splice(currentOperationIndex.value, 1);
    closeModal();
    confirmDeleteModal.value = false;
    render.value++;
    localStorage.setItem('detailsData',JSON.stringify(details.value))
}
function Deletion() {
    confirmDeleteModal.value = false;
    closeModal()
}
function closeModal() {
    isModalVisible.value = false;
    currentOperation.value = null;
    currentOperationIndex.value = null;
}

</script>
  
<style>
.head {
    margin-bottom: 10px;
}

.form-container {
    max-width: 300px;
    margin: 0 auto;
}

.delete-container {
    text-align: center;
    margin-bottom: 10px;
}

.details-table {
    width: 80%;
    border-collapse: collapse;
    margin-top: 20px;
}

.details-table th,
.details-table td {
    border: 1px solid #ddd;
    padding: 10px;
    text-align: left;
}

.details-table th {
    background-color: #f2f2f2;
}

.details-table td {
    background-color: #fff;
}

.details-table button {
    margin-right: 5px;
}
</style>
  
  
  
  
  
  
  
   
   

  