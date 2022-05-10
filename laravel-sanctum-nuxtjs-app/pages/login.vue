
<template>
  <section class="section">
    <div class="container">
      <div class="columns is-centered">
        <div class="column is-one-third">
          <h2 class="title has-text-centered">Login</h2>

          <form method="post" @submit.prevent="login">
            <b-field label="Email">
              <b-input
                type="email"
                v-model="email"
                required>
              </b-input>
            </b-field>

            <b-field label="Password">
              <b-input
                type="password"
                v-model="password"
                password-reveal
                required>
              </b-input>
            </b-field>

            <b-button type="is-dark is-fullwidth" native-type="submit">
              Login
            </b-button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>


<script>
export default {
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    async login() {
      await this.$auth.loginWith('laravelSanctum', {
        data: {
          email: this.email,
          password: this.password,
        },
      })

     this.$router.push('/')
    },
  },
}
</script>
