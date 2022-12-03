<template>
  <div class="container">
    <div class="row mb-2 d-flex justify-content-center">
      <div class="col-xs-12 co-sm-12 col-md-12 col-lg-6 col-xl-6">
        <div class="card mb-4 border-primary">
          <div class="card-header bg-primary text-white d-flex justify-content-between">
            <div class="">Usuario</div>
          </div>
          <div class="card-body table-responsive">
            <router-link class="btn btn-primary me-2" to="/createusuario">Nuevo Usuario</router-link>
            <div class="text-center" v-show="isLoading">
              <div class="spinner-border text-primary" role="status">
                <span class="visually-hidden">Cargando informacion</span>
              </div>
            </div>
  
  
            <table class="table" v-show="!isLoading">
              <thead>
              <tr>
                <th scope="col">Nombre</th>
                <th scope="col">Apellido</th>
                <th scope="col">Correo</th>
                <th scope="col">Contraseña</th>
                <th scope="col">Estado</th>
                <th scope="col">Google</th>
                <th scope="col">Imagen</th>
                <th scope="col">Fecha de Nacimiento</th>
                <th scope="col">Direccion</th>
                <th scope="col">Telefono</th>
                <th scope="col">Rol</th>
                <th scope="col">Genero</th>
                <th scope="col">Categoria</th>
              </tr>
              </thead>
              <tbody>
              <tr v-for="user in users" v-bind:key="user">
                <th scope="row">{{user.name}}</th>
                <td>
                  <router-link class="btn btn-primary me-2" :to="'/editusuario/'+categorie._id"> Editar</router-link>
                  <router-link class="btn btn-danger me-2" :to="'/removeusuario/'+categorie._id"> Borrar</router-link>
                </td>
              </tr>
  
              </tbody>
            </table>
          </div>
          </div>
          </div>
      </div>
  </div>
  </template>
  
  <script>
  export default {
    name: "UsuarioView",
    data() {
      return {
        users:[],
        isLoading: false
      }
    },
    async mounted(){
      this.isLoading = true;
      await this.axios.get('/users')
          .then(response =>  {
            const {users} =response.data;
            this.users = users;
          });
      this.isLoading = false;
    }
  }
  </script>
  
  <style scoped>
  </style>

<
</style>