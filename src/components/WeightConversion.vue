<template>

  <div id="weight-conversion">
    <h1>Weight Conversion</h1>
    <div id = "databinding">
      <h3>Convert from:</h3>
      <select id="convert_from_unit" v-model = "convertfrom">
        <option v-for = "option in units"  :value="option.name" :key="option.name"> {{option.desc}} </option><br/>
      </select><br/>
      <h3>Convert to:</h3>
      <select id="convert_to_unit"  v-model = "convertto">
        <option v-for = "option in units" :value="option.name" :key="option.name">{{option.desc}}</option>
      </select><br/><br/>
      <h2><input type="number" id="input_amount" min="0" v-model="amount" placeholder = "Enter amount" /> {{convertfrom}} = {{finalamount}} {{convertto}}</h2>
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
          final = this.amount;
        }
        break;
        
        case "lbs":
        if (to == "kg") {
          final = Math.round((this.amount * 0.45359237) * 100) / 100;
        } if (to == "st") {
          final = Math.round((this.amount * 0.0714285714) * 100) / 100;
        }  if (to == "lbs") {
          final = this.amount;
        }
        break;

        case "st":
        if (to == "kg") {
          final = Math.round((this.amount * 6.35029318) * 100) / 100;
        } if (to == "lbs") {
          final = Math.round((this.amount * 14) * 100) / 100;
        }  if (to == "st") {
          final = this.amount;
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
  margin: 0 auto;
  border-radius: 5px;
  width: 40%;
  background-color: aliceblue;
  -webkit-box-shadow: 0px 0px 85px 2px rgba(0,0,0,0.63);
  -moz-box-shadow: 0px 0px 85px 2px rgba(0,0,0,0.63);
  box-shadow: 0px 0px 85px 2px rgba(0,0,0,0.63);
  min-width: 400px;
}

h1 {
  font-size: 3em;
  color: aliceblue;
  background-image: linear-gradient(to right bottom, #a8c1e7, #a0b2d9, #98a3ca, #9094bb, #8886ac);
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


</style>
