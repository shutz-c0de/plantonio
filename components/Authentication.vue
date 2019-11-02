<template>
    <button @click="AuthProvider"></button>
</template>

<script>
export default {
  components: {
    LoginBtn
  },
  data: {
    outputText: 'Hello Vue.js!'
  },
  methods: {
    AuthProvider: function () {
        const authenticator = new netlify.default ({})
        authenticator.authenticate({provider:"github", scope: "user"}, (err, data) => {
            err ? this.outputText = "Error Authenticating with GitHub: " + err : 
            this.outputText = "Authenticated with GitHub. Access Token: " + data.token
        })
    }
  }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

</style>
