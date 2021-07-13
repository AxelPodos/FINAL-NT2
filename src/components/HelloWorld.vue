<template>
<div class="codificacion">
    <h4><u>EXAMEN FINAL INPUT</u></h4>     
        <input type="text" :value="string" @input="actualizar($event)"> <br>
        <br>
        <h4> CANTIDAD DE LETRAS : {{ string.length }}</h4>
        <br>
        <h4> CODIFICADO: {{word1 | codif}} </h4>
        <br>
        <h4> MAYUSCULA: {{word2 | mayus}} </h4>
        <br>
        <h4> MINUSCULA: {{word3 | minusc}} </h4>
        <br>
        <h4> INTERCALADAS EMPEZANDO POR MAYUSCULA: {{word4 | INTERMAYUS}} </h4>
        <br>
        <h4> INTERCALADAS EMPEZANDO POR MINUSCULA: {{word5 | INTERMINUS}} </h4>
        
        <BR></BR>

        <p> RESPUESTA MULTIPLE CHOICE: 1:B, 2:B , 3:C, 4:B, 5:B,C</p>
  </div>
</template>

<script>
export default {
  name: 'Codificacion',
  data() {
    return {
        string:"",
        word1: '',
        word2: '',
        word3: '',
        word4: '',
        word5: '',     
    }
  },
  methods: {
    actualizar(valor) {
          let dato = valor.target.value      
          this.string = dato
          this.word1 = dato
          this.word2 = dato
          this.word3 = dato
          this.word4 = dato
          this.word5 = dato
      }
    },
  computed: {

    },
  filters: {
    codif: function (value) {
      if (!value) return ''
      let rta = value.split("a").map(s => s.split("u").join("a")).join("u").split("e").map(s => s.split("o").join("e")).join("o")
      return rta        
    },
    mayus: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.toUpperCase()
    },
    minusc: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.toLowerCase()
    },
    INTERMAYUS: function (value) {
          var letter = '';
          for (var i = 0; i < value.length; i++) {
            if(i % 2 === 0){
              letter += value.charAt(i).toUpperCase();
            } else {
              letter += value.charAt(i).toLowerCase();
            }
        }
          return letter;
    },
    INTERMINUS: function (value) {
        var letter = '';
        for (var i = 0; i < value.length; i++) {
          if(i % 2 !== 0){
            letter += value.charAt(i).toUpperCase();
          } else {
            letter += value.charAt(i).toLowerCase();
          }
      }
        return letter;
    },
  },
}
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
