<template>
  <div>
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Email</th>
          <th>Phone</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" v-bind:key="user.email">
          <td><router-link :to="{ name: 'user', params: { id: user.login.username } }">{{ user.name.first }} {{ user.name.last }}</router-link></td>
          <td>{{ user.email }}</td>
          <td>{{ user.phone }}</td>
        </tr>
      </tbody>
    </table>
    <button @click="fetchUsers">Load more...</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: []
    }
  },
  created() {
    this.fetchUsers();
  },
  methods: {
    fetchUsers: function() {
      fetch('https://randomuser.me/api?results=20')
        .then(response => response.json())
        .then(response => {
          this.users = this.users.concat(response.results);
        });
    }
  },
}
</script>