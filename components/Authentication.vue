<template>
  <button @click="authProvider">THE BUTTON</button>
</template>

<script>
import netlify from 'netlify-auth-providers'

export default {
  data() {
    return { outputText: 'Hello Vue.js!' }
  },
  methods: {
    authProvider() {
      const authenticator = new netlify.Default({})
      authenticator.authenticate(
        { provider: 'github', scope: 'user' },
        (err, data) => {
          err
            ? (this.outputText = 'Error Authenticating with GitHub: ' + err)
            : (this.outputText =
                'Authenticated with GitHub. Access Token: ' + data.token)
        }
      )
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
