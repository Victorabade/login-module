<template>
  <div class="login-container">
    <h2>Login</h2>
    <form @submit.prevent="login">
      <div>
        <label for="username">Usuário:</label>
        <input v-model="username" type="text" id="username" required />
      </div>
      <div>
        <label for="password">Senha:</label>
        <input v-model="password" type="password" id="password" required />
      </div>
      <button type="submit">Entrar</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'LoginPage',
  data() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    async login() {
      try {
        // Substituir pela sua chamada real de autenticação
        const response = await this.$axios.post('/api/auth/login', {
          username: this.username,
          password: this.password
        })

        // Após login bem-sucedido, navegar para a home
        this.$router.push('/home')
      } catch (error) {
        alert('Falha no login')
      }
    }
  }
}
</script>

<style scoped>
.login-container {
  max-width: 300px;
  margin: 100px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #213547;
}
input {
  width: 100%;
  margin-bottom: 10px;
  padding: 8px;
  box-sizing: border-box;
}
button {
  width: 100%;
  padding: 8px;
}
</style>