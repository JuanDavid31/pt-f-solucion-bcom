<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <h3 class="text-center my-4">Usuarios</h3>
        <table id="tabla" class="ml- w-100 table table-striped">
          <thead class="text-center">
            <tr>
              <th scope="col" class="m-0 p-2">Id</th>
              <th scope="col" class="m-0 p-2">Nombre</th>
              <th scope="col" class="m-0 p-2">Fecha creacion</th>
              <th scope="col" class="m-0 p-2">fecha edicion</th>
              <th scope="col" class="m-0 p-2">-</th>
              <th scope="col" class="m-0 p-2">-</th>
            </tr>
          </thead>
          <tbody class="text-center">
            <tr v-for="(usu, index) in usuarios" :key="index">
              <th class="px-2 my-2">{{ usu.id }}</th>
              <td class="my-2">{{ usu.nombre }}</td>
              <td class="my-2">{{ usu.fecha_creacion.split("T")[0] }}</td>
              <td class="my-2">{{ usu.fecha_edicion.split("T")[0] }}</td>
              <td>
                <button
                  class="btn btn-outline-secondary my-1 py-0"
                  v-on:click="editar(`${usu.id}`)"
                >
                  Editar
                </button>
              </td>
              <td>
                <button
                  class="btn btn-outline-secondary my-1 py-0"
                  v-on:click="eliminar(`${usu.id}`)"
                >
                  Eliminar
                </button>
              </td>
            </tr>
          </tbody>
        </table>
        <button
          v-on:click="guardar"
          class="btn btn-outline-secondary mt-4 w-100"
        >
          Agregar Usuario
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue } from "vue-class-component";
export default class Home extends Vue {
  usuarios = [];
  usuario = {};
  usuarioSelect = {};

  created() {
    console.log("Aquí inicializamos el servicio");
  }

  mounted() {
    console.log("Aquí cargamos los usuarios");
  }

  guardar() {
    this.$router.push("/usuarios/nuevo");
  }
}
</script>
