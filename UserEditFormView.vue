<template>
    <div class="container">
      <div class="row mb-2 d-flex justify-content-center">
        <div class="col-xs-12 co-sm-12 col-md-12 col-lg-6 col-xl-6">
          <div class="card mb-4 border-primary">
            <div class="card-header bg-primary text-white d-flex justify-content-between">
              <div class="">Usuario </div>
            </div>
            <div class="card-body ">
              <div class="alert alert-success" role="alert" v-show="showSuccess">
               Usuario Guardado correctamente.
              </div>
  
              <div class="alert alert-danger" role="alert" v-show="showError">
                A ocurrido un error, Usuario no guardado
                <br>
                <strong>{{errorMessage}}</strong>
  
                <ul >
                  <li v-for="(errors, index) in errorsMessages" :key="index">{{errors.param}}: {{errors.msg}}</li>
                </ul>
              </div>
  
              <div class="text-center" v-show="isLoading">
                <div class="spinner-border text-primary" role="status">
                  <span class="visually-hidden">Cargando datos</span>
                </div>
              </div>
  
              <div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="name" class="form-label">Nombre de Usuario</label>
                  <input type="text" class="form-control" id="name" name="name" placeholder="Nombre de Usuario" v-model="name">
                </div>
              </div>
              <div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="lastname" class="form-label">Apellido de Usuario</label>
                  <input type="text" class="form-control" id="lastname" name="lastname" placeholder="Apellidos de Usuario" v-model="lastname">
                </div>
              </div><div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="email" class="form-label">Correo</label>
                  <input type="text" class="form-control" id="email" name="email" placeholder="Correo" v-model="email">
                </div>
              </div><div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="pass" class="form-label">Contraseña</label>
                  <input type="text" class="form-control" id="pass" name="pass" placeholder="Contraseña" v-model="pass">
                </div>
              </div><div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="name" class="form-label">Estado</label>
                  <input type="text" class="form-control" id="state" name="state" placeholder="Estado" v-model="state">
                </div>
              </div><div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="gogl" class="form-label">Google</label>
                  <input type="text" class="form-control" id="gogl" name="gogl" placeholder="Google" v-model="gogl">
                </div>
              </div><div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="img" class="form-label">Imagen</label>
                  <input type="text" class="form-control" id="img" name="img" placeholder="Imagen" v-model="img">
                </div>
              </div><div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="birtdate" class="form-label">Fecha de Nacimiento</label>
                  <input type="text" class="form-control" id="birtdate" name="birtdate" placeholder="Fecha de Nacimiento" v-model="birtdate">
                </div>
              </div><div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="addrs" class="form-label">Direccion</label>
                  <input type="text" class="form-control" id="addrs" name="addrs" placeholder="Direccion" v-model="addrs">
                </div>
              </div><div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="telpn" class="form-label">Telefono</label>
                  <input type="text" class="form-control" id="telpn" name="telpn" placeholder="Telefono" v-model="telpn">
                </div>
              </div><div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="rol" class="form-label">Rol</label>
                  <input type="text" class="form-control" id="rol" name="rol" placeholder="Rol" v-model="rol">
                </div>
              </div><div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="gender" class="form-label">Genero</label>
                  <input type="text" class="form-control" id="gender" name="gender" placeholder="Genero" v-model="gender">
                </div>
              </div><div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12">
                  <label for="categorie" class="form-label">Categoria</label>
                  <input type="text" class="form-control" id="categorie" name="categorie" placeholder="Categoria" v-model="categorie">
                </div>
              </div>
  
              <div class="row mb-3">
                <div class="col-sm-12 col-md-12 col-lg-12 col-xl-12 text-center">
                  <button class="btn btn-primary" @click="saveUser">Guardar</button>
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
    name: "UsuariosEditFormView",
    data() {
      return {
        isLoading: false,
        name: '',
        lastname:'',
        email:'',
        pass:'',
        state:'',
        gogl:'',
        img:'',
        birtdate:'',
        addrs:'',
        telpn:'',
        rol:'',
        gender:'',
        categorie:'',
        showError: false,
        showSuccess: false,
        errorMessage: '',
        errorsMessages: [],
        uiditems: ""
      }
    },
    methods: {
      async saveUser () {
        let params = {
          name: this.name,
          lastname: this.lastname,
          email:this.email,
          pass:this.pass,
          state:this.state,
          gogl:this.gogl,
          img:this.img,
          birtdate:this.birtdate,
          addrs:this.addrs,
          telp:this.telpn,
          rol:this.rol,
          gender:this.gender,
          categorie:this.categorie
        };
        this.showError = false;
        this.showSuccess = false;
        this.isLoading = true;
        await this.axios.put(`/users/${this.uiditems}`, params)
            .then(res => {
              this.showSuccess = true;
              this.$router.push("/usuarios");
            })
            .catch(err => {
              const {errors, message} = err.response.data;
              this.errorsMessages = errors;
              this.errorMessage = message;
              this.showError = true;
            })
        this.isLoading = false;
      },
      async getDataParams(uid){
        await this.axios.get(`/users/usuarioid/${uid}`)
            .then(response =>  {
              const {usuario} = response.data;
              const { name } = usuario;
              this.name = name;
            });
      }
    },
    async mounted(){
      this.uiditems = this.$route.params.uid;
      this.getDataParams(this.$route.params.uid);
    },
  }
  </script>
  
  <style scoped>
  </style>