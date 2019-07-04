<template>

  <div id="weight-conversion">

    <div class="header">
      <h1>Weight Conversion</h1>
    </div>
    <div class="unit_from">
      <h3>Convert from:</h3>
        <select id="convert_from_unit" v-model = "convertfrom">
          <option v-for = "option in units"  :value="option.name" :key="option.name"> {{option.desc}} </option><br/>
        </select><br/>
    </div>
    <div class="unit_to">
      <h3>Convert to:</h3>
        <select id="convert_to_unit"  v-model = "convertto">
          <option v-for = "option in units" :value="option.name" :key="option.name">{{option.desc}}</option>
        </select><br/><br/>
    </div>
    <div class="input_amount">
      <input type="number" id="input_amount" min="0" v-model="amount" placeholder = "Enter amount" />
    </div>
    <div class="result">
     {{convertfrom}} = {{finalamount.toPrecision(5)}} {{convertto}}
    </div>
  </div>
  
</template>

<script>
export default {
  data() {
    return {
      name:'',
      units: [
        {name:"kg", desc:"kilogram"},
        {name:"lbs", desc:"pounds"},
        {name:"st", desc:"stones"},
        ],
      convertfrom: "kg",
      convertto:"st",
      amount:""
    }
  },
  computed: {
    finalamount:function() {
      var to = this.convertto;
      var from = this.convertfrom;
      var final;
      switch(from) {
        case "kg":
        if (to == "lbs") {
          final = Math.round((this.amount * 2.20462262) * 100) / 100;
        } if (to == "st") {
          final = Math.round((this.amount * 0.157473044) * 100) / 100;
        }  if (to == "kg") {
          final = this.amount*1;
        }
        break;
        
        case "lbs":
        if (to == "kg") {
          final = Math.round((this.amount * 0.45359237) * 100) / 100;
        } if (to == "st") {
          final = Math.round((this.amount * 0.0714285714) * 100) / 100;
        }  if (to == "lbs") {
          final = this.amount*1;
        }
        break;

        case "st":
        if (to == "kg") {
          final = Math.round((this.amount * 6.35029318) * 100) / 100;
        } if (to == "lbs") {
          final = Math.round((this.amount * 14) * 100) / 100;
        }  if (to == "st") {
          final = this.amount*1;
        }
        break;
        }
        return final;
      }
  },
  methods: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#weight-conversion {
  padding-bottom: 10px;
  margin: auto;
  border-radius: 5px;
  width: 40%;
  height: 50%;
  background-color: aliceblue;
  box-shadow: 0px 1px 19px 3px rgba(0, 0, 0, 0.35);
  min-width: 400px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 0.5fr 0.5fr 0.5fr;
  grid-template-areas: "header header" "unit_from unit_from" "unit_to unit_to" "input_amount result";
}

h1 {
  font-size: 3em;
  color: aliceblue;
  background-color: #556E99;
  margin-top: 0px;
  padding: 30px 0;
  border-radius: 5px 5px 0 0;
}

#input_amount {
  width: 8em;
  height: 30px;
  font-size: 20px;
  text-align: center;
  font-family: 'Maven Pro', Helvetica, Arial, sans-serif;
  border-radius: 9px;
  -webkit-appearance: none;
  float: right;
  grid-area: input_amount; 
  margin: auto 0;
}

#convert_from_unit{
  width: 10em;
  padding: 12px 20px;
  border-radius: 9px;
}

#convert_to_unit{
  width: 10em;
  padding: 12px 20px;
  border-radius: 9px;
}

.header { 
  grid-area: header; 
}

.unit_from { 
  grid-area: unit_from; 
}

.unit_to { 
  grid-area: unit_to; 
}

.input_amount { 
  grid-area: input_amount; 
  margin: auto 0;
}

.result { 
  grid-area: result;
  text-align: left; 
  margin: auto 0;
}


</style>
