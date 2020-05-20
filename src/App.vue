<template>
<div id = "back" style = "">
   <h1>Currency Converter</h1>
   <span>Enter Amount:</span><input type = "number" v-model.number = "amount" placeholder = "Enter Amount" /><br/><br/>
    <h3>Choose the currency:</h3><br>
   <span>Convert From:</span>
   <select v-model = "convertfrom">
     <option v-for = "(c, index) in currencyfrom" v-bind:value = "c.name">{{c.money}}</option>
   </select>
   <span> Convert To:</span>
   <select v-model = "convertto">
     <option v-for = "(c, index) in currencyfrom" v-bind:value = "c.name">{{c.money}}</option>
   </select><br/><br/>
   <span> {{amount}} {{convertfrom}} equals {{finalamount}} {{convertto}}</span>
</div>
</template>
<script>
export default {
     data(){
       return{
        name:'',
        currencyfrom : [
          {name:"USD", money:"US Dollar"},
          {name:"EUR", money:"Euro"},
          {name:"INR", money:"Indian Rupee"},
          {name:"BHD", money:"Bahraini Dinar"}
          ],
        convertfrom: "INR",
        convertto:"USD",
        amount :""
       };
     },
     
   computed :{
     finalamount:function() {
       var to = this.convertto;
       var from = this.convertfrom;
       var final;
       switch(from) {
         case "INR":
           if (to == "USD") {
             final = this.amount * 0.016;
           }
           if (to == "EUR") {
             final = this.amount * 0.013;
           }
           if (to == "INR") {
             final = this.amount;
           }
           if (to == "BHD") {
             final = this.amount * 0.0059;
           }
           break;
         case "USD":
           if (to == "INR") {
             final = this.amount * 63.88;
           }
           if (to == "EUR") {
             final = this.amount * 0.84;
           }
           if (to == "USD") {
             final = this.amount;
           }
           if (to == "BHD") {
             final = this.amount * 0.38;
           }
           break;
         case "EUR":
           if (to == "INR") {
             final = this.amount * 76.22;
           }
           if (to == "USD") {
             final = this.amount * 1.19;
           }
           if (to == "EUR") {
             final = this.amount;
           }
           if (to == "BHD") {
             final = this.amount * 0.45;
           }
           break;
         case "BHD":
           if (to == "INR") {
             final = this.amount *169.44;
           }
           if (to == "USD") {
             final = this.amount * 2.65;
           }
           if (to == "EUR") {
             final = this.amount * 2.22;
           }
           if (to == "BHD") {
             final = this.amount;
           }
           break
       }
       return final;
     }
   }
  };
</script>
