<script setup>
import router from "../router";
import { useUsuariosStore } from "../stores/usuarios.js";

const usuariosStore = useUsuariosStore();

const enviarRegistro = async () => {
  await usuariosStore.enviarRegistro();
  router.push("/login");
};

</script>

<template>
  <main>

    <head>
      <meta charset="UTF-8" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    </head>

    <body>
      <div class="formulario-centrado bg-primary-subtle ">
        <form @submit.prevent="enviarRegistro">
          <div class="form-group">
            <label for="email">
              <h3>Email:</h3>
            </label><br />
            <input type="email" class="form-control form-control-lg" id="email" placeholder="Ingresa email"
              v-model="usuariosStore.usuario.email" /><br />
          </div>
          <div class="form-group">
            <label for="password">
              <h3>Contraseña:</h3>
            </label>
            <input type="password" class="form-control form-control-lg" id="password" placeholder="Ingresa contraseña"
              v-model="usuariosStore.usuario.password" /><br />
          </div>
          <button type="submit" class="btn btn-primary btn-lg">
            Registrate
          </button>
        </form>
      </div>
    </body>
  </main>
</template>


<style>
.formulario-centrado {
  min-height: 50vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
