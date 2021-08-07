<template>
  <div>
    Here is how the received payload is looking (Array of Objects)
    <pre>{{ users }}</pre>
    <div>
      -------------
      <p v-for="user in users" :key="user.id">
        name: <span>{{ user.name }}</span> and email: {{ user.email }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [],
    }
  },
  async fetch() {
    // $get is a shortcut for `.data` as shown here: https://axios.nuxtjs.org/usage#-shortcuts
    const usersResult = await this.$axios.$get(
      'https://jsonplaceholder.typicode.com/users'
    )
    console.log('what we have received', usersResult)
    this.users = usersResult
  },
}
</script>
