<template>
  <div class="final">
    <input type="text" :value="input" @input="actualizar($event)" /> <br />
    <h4>cantidad: {{ input.length }}</h4>
    <h4>{{ first | codificar }}</h4>
    <h4>{{ second | uppercase }}</h4>
    <h4>{{ third | lowercase }}</h4>
    <h4>{{ four | mezclando1 }}</h4>
    <h4>{{ five | mezclando2 }}</h4>
    <br />
    <hr />
    <p>Respuestas: 1:b, 2:b , 3:c, 4:b, 5:b,c</p>
  </div>
</template>

<script>
export default {
  name: "Codificacion",
  data() {
    return {
      input: "",
      first: "",
      second: "",
      third: "",
      four: "",
    };
  },
  methods: {
    actualizar(e) {
      let ingresando = e.target.value;
      this.input = ingresando;
      this.first = ingresando;
      this.second = ingresando;
      this.third = ingresando;
      this.four = ingresando;
      this.five = ingresando;
    },
  },
  computed: {},
  filters: {
    uppercase: function(value) {
      if (!value) return "";
      value = value.toString();
      return value.toUpperCase();
    },
    lowercase: function(value) {
      if (!value) return "";
      value = value.toString();
      return value.toLowerCase();
    },
    mezclando1: function(value) {
      value = String(value);
      var flip = "";
      for (var i = 0; i < String(value).length; i++) {
        if (i % 2 === 0) {
          flip += value.charAt(i).toUpperCase();
        } else {
          flip += value.charAt(i).toLowerCase();
        }
      }
      return flip;
    },
    mezclando2: function(value) {
      value = String(value);
      var flip = "";
      for (var i = 0; i < String(value).length; i++) {
        if (i % 2 !== 0) {
          flip += value.charAt(i).toUpperCase();
        } else {
          flip += value.charAt(i).toLowerCase();
        }
      }
      return flip;
    },
    codificar: function(value) {
      let palabraAModificar = "";
      let palabralowercase = value.toLowerCase();
      for (let i = 0; i < String(value).length; i++) {
        let letra = palabralowercase[i];
        switch (letra) {
          case "a":
            letra = "u";
            break;
          case "e":
            letra = "o";
            break;
          case "o":
            letra = "e";
            break;
          case "u":
            letra = "a";
            break;
        }
        palabraAModificar += letra;
      }
      return palabraAModificar;
    },
  },
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
