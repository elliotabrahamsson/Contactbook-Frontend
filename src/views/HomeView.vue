<script>
export default {
  methods: {
    addContact() {
      let name = document.getElementById("name").value;
      let phone = document.getElementById("phone").value;

      fetch("/contact", {
        method: "POST",
        body: JSON.stringify({ name: name, phone: phone }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      }).then(async (res) => {
        console.log("added" + (await res.json()));
      });
    },
    showContacts() {
      fetch("/contact").then(async (res) => {
        let contacts = (await res.json()).contacts;
        let contactDiv = document.getElementById("contacts");
        contactDiv.innerText = "";
        contacts.forEach((contact) => {
          contactDiv.innerText += JSON.stringify(contact) + "\n";
        });
      });
    },
    getContact() {
      let contactId = document.getElementById("contactId").value;
      let contactSearch = document.getElementById("contactSearch");

      fetch(`/contact/${contactId}`).then(async (res) => {
        let contact = await res.json();
        contactSearch.innerText = JSON.stringify(contact);
      });
    },
  },
};
</script>

<template>
  <form method="post">
    <input type="text" id="name" name="name" placeholder="name" />
    <input type="text" id="phone" name="phone" placeholder="phone number" />
    <button type="button" v-on:click="addContact()">Add contact</button>
  </form>

  <button v-on:click="showContacts()">Show contacts</button>
  <div id="contacts"></div>

  <form method="get">
    <input type="number" id="contactId" name="id" placeholder="input ID" />
    <button type="button" v-on:click="getContact()">Get contact</button>
  </form>
  <div id="contactSearch"></div>
</template>
