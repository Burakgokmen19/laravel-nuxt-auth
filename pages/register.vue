<template>
  <div class="container mt-5">
    <div class="row justify-content-center">
      <div class="col-md-6">
        <div class="card">
          <div class="card-header">Kayıt Ol</div>
          <div class="card-body">
            <form @submit.prevent="register">
              <div class="mb-3">
                <label for="email" class="form-label">E-posta:</label>
                <input v-model="email" type="email" class="form-control" id="email" required>
              </div>
              <div class="mb-3">
                <label for="password" class="form-label">Şifre:</label>
                <input v-model="password" type="password" class="form-control" id="password" required>
              </div>
              <div class="d-grid">
                <button type="button"  @click="register" class="btn btn-primary">Kayıt Ol</button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
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
    async register() {
      try {
        await this.$auth.register('laravelSanctum', {
          email: this.email,
          password: this.password,
        })


        this.$router.push('/login')
      } catch (error) {
        console.error('Kayıt hatası:', error)
      }
    },
  },
}
</script>
