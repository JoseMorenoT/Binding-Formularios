<template>
  <div class="contenedorTarjeta">
    <form>
      <div>
        <label>Título de la tarjeta: </label>
        <input v-model="tituloTarjeta" />
      </div>

      <div>
        <label>Chip SRC: </label>
        <input v-model="chipSRC" disabled />
      </div>

      <div>
        <label>Número: </label>
        <input v-model="numero" />
      </div>

      <div>
        <label>Fecha de expiración: </label>
        <input v-model="fechaExpiracion" />
      </div>

      <div>
        <label>Propietario: </label>
        <input v-model="propietario" />
      </div>

      <div>
        <label>Tipo de tarjeta SRC: </label>
        <select name="credit" id="credit" v-model="tipoTarjetaSRC">
          <!-- se repite n cantidad de veces -->
          <option v-for="credit in credits" :key="credit.id"
            :value="credit.path">{{ credit.texto }}</option>
        </select>
      </div>
    </form>

    <div class="tarjeta">
      <h3>{{ tituloTarjeta }}</h3>
      <img width="40" :src="require('../assets/img/chip.png')" alt="" />
      <div>
        <h2>{{ numero }}</h2>
        <span
          >Fecha Exp: <b>{{ fechaExpiracion }}</b></span
        >
      </div>
      <footer>
        <span>{{ propietario }}</span>
        <img :src="tipoTarjetaSRC" width="60" />
      </footer>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardTarjeta",
  data() {
    return {
      tituloTarjeta: "Visa",
      chipSRC: require("../assets/img/chip.png"),
      numero: "",
      fechaExpiracion: "",
      propietario: "",
      tipoTarjetaSRC: "https://cdn3.bci.cl/uploads/3b38f004-2f00-4be8-a5d8-bae29e76c565/original/Icon_Avance_Dic.png",
      credits: [
          { id: 1, path: require("../assets/img/visa.png"), texto: "Visa" },
          { id: 2, path: require("../assets/img/Mastercard.png"), texto: "Mastercard" },
          { id: 3, path: require("../assets/img/AmericanExpress.png"), texto: "American Express" },
        ],
    }
  }
};
</script>

<style scoped>
* {
    margin: 0;
}
.contenedorTarjeta {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 60vh;
    font-size: 10px;
    font-family: sans-serif;
    gap: 40px;
}

form {
    padding: 18px;
    border-radius: 20px;
    border: ridge 1px;
    box-shadow: 1px 1px 1px 1px gray;
    font-weight: bold;
    display: flex;
    flex-direction: column;
    gap: 15px;
    justify-content: center;
}
form div {
    display: grid;
    grid-template-columns: 100px 200px;
    align-items: center;
    gap: 5px;
}

form div label {
    text-align: right;
}

.tarjeta {
    width: 400px;
    height: 230px;
    background: #1c1a1e;
    color: white;
    border-radius: 20px;
    padding: 20px;
    box-shadow: 0px 0px 10px 2px black;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

h3 {
    font-size: 20px;
}

h2 {
    font-size: 30px;
    letter-spacing: 10px;
    margin-bottom: 15px;
    text-shadow: 0px 0px 1px gold;
    font-family: Times;
}

b {
    font-size: 16px;
}

footer {
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    font-weight: bold;
    font-size: 18px;
    text-transform: uppercase;
    font-style: italic;
}
</style>
