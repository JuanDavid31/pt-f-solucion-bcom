<template>
  <div class="container">
    <div class="row d-flex justify-content-center">
      <div class="col-10 border rounded my-5">
        <h5 class="mt-4 text-center">Nuevo Usuario</h5>
        <form class="mt-4 m-2">
          <div class="form-group row">
            <label
              for="inputNombre"
              class="text-center col-sm-2 col-form-label my-3"
              >Nombre</label
            >
            <div class="col mr-3 my-3">
              <input
                type="text"
                class="form-control"
                id="inputNombre"
                v-model="usuario.nombre"
              />
            </div>
          </div>
          <div class="form-group row">
            <label
              for="inputFechaC"
              class="text-center col-sm-2 col-form-label my-3"
              >Fecha Creacion</label
            >
            <div class="col mr-3 my-3">
              <input
                type="date"
                class="form-control"
                id="inputFechaC"
                v-model="usuario.fecha_creacion"
              />
            </div>
          </div>
          <div class="form-group row">
            <label
              for="inputFechaE"
              class="text-center col-sm-2 col-form-label my-3"
              >Fecha Edicion</label
            >
            <div class="col mr-3 my-3">
              <input
                type="date"
                class="form-control"
                id="inputFechaE"
                v-model="usuario.fecha_edicion"
              />
            </div>
          </div>
          <button
            @click="guardar"
            class="btn btn-outline-secondary w-100 mb-3"
            type="button"
          >
            guardar
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
import Usuario from "@/classes/Usuario";
export default class Home extends Vue {
  usuario!: Usuario;

  guardar() {
    let url = `${process.env.VUE_APP_API_URL}/usuarios/guardar`;
    fetch(url, {
      method: "POST",
      body: JSON.stringify(this.usuario),
      headers: { "Content-Type": "application/json" },
    })
      .then((data) => this.redirigir())
      .catch((error) => alert(error));
  }

  redirigir() {
    this.$router.push("/usuarios");
  }
}
</script>
