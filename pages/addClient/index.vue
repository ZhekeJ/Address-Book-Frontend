<template>
  <div>
    <h1 class="hmain">Add New Client</h1>
    <FormulateForm
      class="formFormulate"
      :schema="schema"
      v-model="formValues"
    />
    <button @click="addClient()" class="btn">Add Client</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formValues: {},
      schema: [
        {
          type: "text",
          label: "Name",
          name: "name",
          validation: "required",
          "outer-class": ["col-span-6", "md:col-span-3"],
        },
        {
          type: "email",
          label: "Email",
          name: "name",
          validation: "required",
          "outer-class": ["col-span-6", "md:col-span-3"],
        },
        {
          type: "text",
          label: "Contact",
          name: "contact",
          validation: "required",
          "outer-class": ["col-span-6", "md:col-span-3"],
        },
        {
          type: "text",
          label: "Company",
          name: "company",
          validation: "required",
          "outer-class": ["col-span-6", "md:col-span-3"],
        },
      ],
    };
  },
  methods: {
    // async addClient() {
    //   const data = await this.$axios.$post("http://localhost:5000/api/clients");

    //   alert("You have successfully added a client into the database");
    // },
    async addClient() {
      axios
        .post("http://localhost:5000/api/clients", {
          name: "Fred",
          email: "jz@gmail.com",
          contact: "zheke",
          company: "zheke pvt",
        })
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>

<style></style>
