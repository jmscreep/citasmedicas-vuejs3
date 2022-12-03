<template>
    <div class="container">
      <div class="row mb-2">
        <div class="col-xs-12 co-sm-12 col-md-12 col-lg-12 col-xl-12">
          <div class="card mb-4 border-primary">
            <div class="card-header bg-primary text-white d-flex justify-content-between">
              <div class="">Usuarios </div>
            </div>
            <div class="card-body text-center">
                <h1 class="fw-bold mb-3">¿Desea Eliminar Este Usuario?</h1>
              <h5 class=" mb-3">Si presiona SI, los datos de usuario se borraran permanente y no se podrán volver a recuperar.</h5>
              <div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12 text-center">
                <button class="btn btn-primary me-2" @click="backScreen">Volver</button>
                <button class="btn btn-danger" @click="removeUsers">SI, ¡Confirmo!</button>
                </div>
              </div>
  
            </div>
  
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "UserRemoveView",
    data() {
      return {
        uiditems: ""
      }
    },
    methods: {
      async removeUsers () {
        await this.axios.delete(`/users/${this.uiditems}`)
            .then(res => {
              this.$router.push("/usuarios");
            })
            .catch(err => {
              const {errors, message} = err.response.data;
            })
      },
      backScreen (){
        this.$router.push("/usuarios");
      }
    },
    async mounted(){
      this.uiditems = this.$route.params.uid;
    },
  }
  </script>
  
  <style scoped>
  </style>