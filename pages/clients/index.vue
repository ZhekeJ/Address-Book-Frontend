<template>
  <!-- <div>
    <ul>
      <li v-for="(client, index) in clients" :key="index">
        {{ client.name }}

        <button class="" @click="deleteClient(client._id)">Delete</button>
        <button @click="addClient">Add</button>
      </li>
    </ul>
    {{ clients }}
  </div> -->
  <div class="flex flex-col">
    <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
      <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
        <div
          class="overflow-hidden border-b border-gray-200 shadow sm:rounded-lg"
        >
          <table class="min-w-full divide-y divide-gray-200">
            <thead class="bg-gray-50">
              <tr>
                <th
                  scope="col"
                  class="px-6 py-3 text-xs font-bold tracking-wider text-left text-gray-500 uppercase "
                >
                  Name
                </th>
                <th
                  scope="col"
                  class="px-6 py-3 text-xs font-bold tracking-wider text-left text-gray-500 uppercase "
                >
                  Email
                </th>
                <th
                  scope="col"
                  class="px-6 py-3 text-xs font-bold tracking-wider text-left text-gray-500 uppercase "
                >
                  Contact
                </th>
                <th
                  scope="col"
                  class="px-6 py-3 text-xs font-bold tracking-wider text-left text-gray-500 uppercase "
                >
                  Company
                </th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="(client, index) in clients"
                :key="index"
                :class="index % 2 === 0 ? 'bg-white' : 'bg-gray-50'"
              >
                <td
                  class="px-6 py-4 text-sm font-medium text-gray-900  whitespace-nowrap"
                >
                  {{ client.name }}
                </td>
                <td class="px-6 py-4 text-sm text-gray-500 whitespace-nowrap">
                  {{ client.email }}
                </td>
                <td class="px-6 py-4 text-sm text-gray-500 whitespace-nowrap">
                  {{ client.contact }}
                </td>
                <td class="px-6 py-4 text-sm text-gray-500 whitespace-nowrap">
                  {{ client.company }}
                </td>
                <td
                  class="px-6 py-4 text-sm font-medium text-right  whitespace-nowrap"
                >
                  <button
                    class="text-indigo-600 hover:text-indigo-900"
                    @click="deleteClient(client._id)"
                  >
                    Delete
                  </button>
                </td>

                <td
                  class="px-6 py-4 text-sm font-medium text-right  whitespace-nowrap"
                >
                  <button
                    class="text-indigo-600 hover:text-indigo-900"
                    @click="updateClient(client._id)"
                  >
                    Update
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
        <div>
          <td
            class="px-6 py-4 text-sm font-medium text-right whitespace-nowrap"
          >
            <nuxt-link
              class="text-indigo-600 hover:text-indigo-900"
              to="/addClient"
            >
              Add New Client</nuxt-link
            >
          </td>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
//import axios from "axios";

export default {
  data() {
    return {
      clients: {},
    };
  },

  mounted() {
    this.fetchClients();
  },
  methods: {
    async fetchClients() {
      const data = await this.$axios.$get("http://localhost:5000/api/clients");
      this.clients = data;
    },

    async deleteClient(id) {
      const data = await this.$axios.$delete(
        "http://localhost:5000/api/clients/" + id
      );

      alert("You have successfully deleted the client details");
    },
  },
};
</script>

<style></style>
