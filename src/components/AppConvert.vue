<template>
  <div class="centered-container background-celeste">
    <img src="@/assets/logo2.png" alt="Mi Logo" class="logo" />
    <div class="container pt-3">
      <div class="row">
        <div class="col-lg-12">
          <div class="form-group">
            <label for="cantidad">Ingrese la cantidad que desea convertir..</label>
            <input
              type="number"
              class="form-control form-control-lg"
              id="cantidad"
              placeholder="Ingrese cantidad.."
              v-model="cantidad"
              v-on:keyup="onChange"
            />
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-lg-6">
          <div class="form-group">
            <label for="tengo">Tengo esta moneda..</label>
            <select
              class="form-control form-control-lg"
              id="tengo"
              v-model="tengo"
              v-on:change="onChange"
            >
              <option v-for="(moneda, index) in monedas" :key="index">
                {{ moneda }}
              </option>
            </select>
          </div>
        </div>
        <div class="col-lg-6">
          <div class="form-group">
            <label for="quiero">Y quiero convertirla a esta moneda...</label>
            <select
              class="form-control form-control-lg"
              id="quiero"
              v-model="quiero"
              v-on:change="onChange"
            >
              <!-- Bucle para mostrar las opciones de las monedas -->
              <option v-for="(moneda, index) in monedas" :key="index">
                {{ moneda }}
              </option>
            </select>
          </div>
        </div>
      </div>
      <div class="text-center pt-4">
        <h5 v-if="cantidad > 0">
          <span class="badge badge-success">{{ cantidad }} {{ tengo }}</span>
          <span class="badge badge-dark"> SON </span>
          <span class="badge badge-success">{{ getTotal(total) }} {{ quiero }}</span>
        </h5>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      monedas: ["USD", "EUR", "LIBRA", "ARS"],
      cantidad: 0,
      tengo: "USD",
      quiero: "EUR",
      total: 0,
    };
  },
  methods: {
    onChange() {
      switch (this.tengo) {
        //Calculos para realizar la conversion de las monedas dependiendo cual quieras cambiar
        case "USD":
          if (this.quiero === "USD") {
            this.total = this.cantidad;
          }
          if (this.quiero === "EUR") {
            this.total = this.cantidad * 372.76;
          }
          if (this.quiero === "LIBRA") {
            this.total = this.cantidad * 429.65;
          }
          if (this.quiero === "ARS") {
            this.total = this.cantidad * 347.19; 
          }
          break;
        case "EUR":
          if (this.quiero === "USD") {
            this.total = this.cantidad * 347.19;
          }
          if (this.quiero === "EUR") {
            this.total = this.cantidad;
          }
          if (this.quiero === "LIBRA") {
            this.total = this.cantidad * 429.65;
          }
          if (this.quiero === "ARS") {
            this.total = this.cantidad * 372.76; 
          }
          break;
        case "LIBRA":
          if (this.quiero === "USD") {
            this.total = this.cantidad * 347.19;
          }
          if (this.quiero === "EUR") {
            this.total = this.cantidad * 372.76;
          }
          if (this.quiero === "LIBRA") {
            this.total = this.cantidad;
          }
          if (this.quiero === "ARS") {
            this.total = this.cantidad * 0.0029; 
          }
          break;
        case "ARS":
          if (this.quiero === "USD") {
            this.total = this.cantidad * 0.0029; 
          }
          if (this.quiero === "EUR") {
            this.total = this.cantidad / 372,76; 
          }
          if (this.quiero === "LIBRA") {
            this.total = this.cantidad / 347.19; 
          }
          if (this.quiero === "ARS") {
            this.total = this.cantidad;
          }
          break;
        default:
      }
    },
    getTotal(valor) {
      return Math.round(valor);
    },
  },
};
</script>

<style scoped>
.centered-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.logo {
  width: 100px;
  height: auto;
  margin-top: -200px; 
}

.background-celeste {
  background-color: lightblue; 
}
.badge {
  margin: 2px;
  font-size: 150%;
}
label {
  font-weight: 700;
  font-size: 130%;
}
</style>
