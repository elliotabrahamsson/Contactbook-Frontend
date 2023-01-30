<script>
function addContact() {}

function showContacts() {}

function getContact() {}
</script>

<template>
  <form method="post">
    <input type="text" name="name" placeholder="name" />
    <input type="text" name="phone" placeholder="phone number" />
    <button type="submit" onclick="addContact()">Add contact</button>
  </form>

  <button onclick="showContacts()">Show contacts</button>

  <form method="get">
    <input type="number" name="id" placeholder="input ID" />
    <button onclick="getContact()">Get contact</button>
  </form>
</template>
