<script>
export default{
data() {
    return {
      item: [
        { id: 1, name: 'Apple Watch', color: 'Gold', category: 'Shiny Watch', price: '$2499' },
        { id: 2, name: 'Apple Car', color: 'Red', category: 'Shiny Car', price: '$9000' },
        { id: 3, name: 'Apple Phone', color: 'Silver', category: 'Shiny Phone', price: '$5499' },
        { id: 4, name: 'Apple TV', color: 'Platinum', category: 'Shiny TV', price: '$1499' },
        // Add more items as needed
      ],
      showModal: false,
      selectedItem: {}
    };
  }
}
</script>

<template>
    <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
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
                        <span class="sr-only">Edit</span>
                        <span class="sr-only">Delete</span>
                    </th>
                </tr>
            </thead>
            <tbody v-for="items in item" :key="items.id">
                <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700">
                    <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white" hidden>
                        {{ items.id }}
                    </th>
                    <td class="px-6 py-4">
                        {{ items.name }}
                    </td>
                    <td class="px-6 py-4">
                        {{ items.color }}
                    </td>
                    <td class="px-6 py-4">
                        {{ items.category }}
                    </td>
                    <td class="px-6 py-4">
                        {{ items.price }}
                    </td>
                    <td class="px-6 py-4 text-right">
                        <a href="#" class="font-medium text-blue-600 dark:text-blue-500 hover:underline">Edit</a>
                    </td>
                </tr>
            </tbody>
        </table>
        <Modal />
    </div>

</template>
