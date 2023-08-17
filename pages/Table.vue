<script>
export default{
data() {
    return {
      items: [
        { id: 1, name: 'Apple Watch', color: 'Gold', category: 'Shiny Watch', price: '$2499' },
        { id: 2, name: 'Apple Car', color: 'Red', category: 'Shiny Car', price: '$9000' },
        { id: 3, name: 'Apple Phone', color: 'Silver', category: 'Shiny Phone', price: '$5499' },
        { id: 4, name: 'Apple TV', color: 'Platinum', category: 'Shiny TV', price: '$1499' },
        // Add more items as needed
      ],
      selectedItem: {}, // Initialize as null
        }
    },
    methods: {
    showModal(item) {
      this.selectedItem = item;
      const modalId = `view-modal-${item.id}`;
      const modal = document.getElementById(modalId);
      if (modal) {
        modal.dataset.modalShow = modalId;
      }
    },
    handleUpdateItem(updatedItem) {
      const index = this.items.findIndex(item => item.id === updatedItem.id);
      if (index !== -1) {
        this.items[index] = updatedItem;
      }
    },
    handleDeleteItem(deletedItem) {
      // Remove the deletedItem from the items array
      this.items = this.items.filter(item => item.id !== deletedItem.id);
    },
  },
}
</script>

<template>
    <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
        <div class="table-container">
            <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
                <caption class="p-5 text-lg font-semibold text-left text-gray-900 bg-white dark:text-white dark:bg-gray-800">
                    Our products
                    <p class="mt-1 text-sm font-normal text-gray-500 dark:text-gray-400">Pasok mga suki, presyong divisoria, sampu sampu, bente trenta, at iba pa.</p>
                </caption>
                <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                    <tr>
                        <th scope="col" class="px-6 py-3" hidden>
                            ID
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Product name
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Color
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Category
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Price
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Actions
                        </th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="item in items" :key="item.id" class="bg-white border-b dark:bg-gray-800 dark:border-gray-700">
                        <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white" hidden>
                            {{ item.id }}
                        </th>
                        <td class="px-6 py-4">
                            {{ item.name }}
                        </td>
                        <td class="px-6 py-4">
                            {{ item.color }}
                        </td>
                        <td class="px-6 py-4">
                            {{ item.category }}
                        </td>
                        <td class="px-6 py-4">
                            {{ item.price }}
                        </td>
                        <td class="px-6 py-4">
        
                        <button @click="showModal(item, 'view-modal')" data-modal-target="view-modal" data-modal-toggle="view-modal" class="text-white bg-gray-800 hover:bg-gray-900 focus:outline-none focus:ring-4 focus:ring-gray-300 font-medium rounded-full text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-gray-800 dark:hover:bg-gray-700 dark:focus:ring-gray-700 dark:border-gray-700" type="button">
                            View
                        </button>
                        <button @click="showModal(item, 'update-modal')" data-modal-target="update-modal" data-modal-toggle="update-modal" class="text-white bg-blue-700 hover:bg-blue-800 focus:outline-none focus:ring-4 focus:ring-blue-300 font-medium rounded-full text-sm px-5 py-2.5 text-center mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800" type="button">
                            Update
                        </button>
                        <button @click="showModal(item, 'delete-modal')" data-modal-target="delete-modal" data-modal-toggle="delete-modal" class="text-white bg-red-700 hover:bg-red-800 focus:outline-none focus:ring-4 focus:ring-red-300 font-medium rounded-full text-sm px-5 py-2.5 text-center mr-2 mb-2 dark:bg-red-600 dark:hover:bg-red-700 dark:focus:ring-red-900" type="button">
                            Delete
                        </button>
                        
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
        <View_Modal :item="selectedItem" />
        <Update_Modal :item="selectedItem" @updateItem="handleUpdateItem" />
        <Delete_Modal :item="selectedItem" @deleteItem="handleDeleteItem" />
    </div>

</template>

<style scoped>
.table-container {
  overflow-x: auto;
}
table {
  min-width: 100%; /* Ensure the table fills the container */
  table-layout: fixed; /* Ensure even column width */
}
thead th {
  position: sticky;
  top: 0;
  background-color: white;
  z-index: 1;
}
</style>
