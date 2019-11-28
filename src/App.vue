<template>
  <div id="app">
    <div style="margin:10% 25%; width: 250px;">
      <br>
      <ejs-autocomplete :dataSource='dataItem' :fields='dataFields'
      placeholder="Select a name" popupWidth="250px" 
      popupHeight="400px" :query='dataQuery' :highlight="true"> 
      </ejs-autocomplete>
    </div>
 </div>
</template>

<script>
import Vue from "vue";
import { AutoCompletePlugin } from "@syncfusion/ej2-vue-dropdowns";
Vue.use(AutoCompletePlugin);
import { DataManager, WebApiAdaptor,
Query } from '@syncfusion/ej2-data';
export default Vue.extend({
  data: function() {
    return {
      //  dataItem: [
      //     { Id: 'Game1', Game: 'Football' },
      //     { Id: 'Game2', Game: 'Basketball'},
      //     { Id: 'Game3', Game: 'Volleyball'},
      //     { Id: 'Game4', Game: 'Baseball' },
      //     { Id: 'Game5', Game: 'Badminton'},
      //   ],
      //  dataFields: { value: 'Game' },
       dataItem: new DataManager({
         url: 'https://ej2services.syncfusion.com/production/web-services/api/Employees',
         adaptor: new WebApiAdaptor,
         crossDomain: true
        }), 
      dataFields:{ value: 'FirstName' },
      dataQuery: new Query().select(['FirstName', 'EmployeeID']).take(9).requiresCount(),
      
    };
  }
}); 
</script>

<style>
@import url(https://cdn.syncfusion.com/ej2/material.css);
</style>
