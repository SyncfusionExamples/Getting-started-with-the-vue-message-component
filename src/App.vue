<script setup>
import { MessageComponent as EjsMessage } from "@syncfusion/ej2-vue-notifications";
import { ButtonComponent as EjsButton } from "@syncfusion/ej2-vue-buttons";
import { ref } from "vue";
const age = ref("");
const isVisible = ref(false);
const messageObj = ref(null);
const dismissClick = function ()
{
  messageObj.value.ej2Instances.visible = false;
}
const inputChange = () =>{ 
   isVisible.value = age.value < 18 || age.value > 60;
};
const content = "Enter a valid age between 18 and 60";
</script>

<template>
   <div class="container">
    <label>Enter your age:</label>
    <div class="inputDiv">
      <input v-model="age" @input="inputChange">
    </div><br>
    <ejs-message ref="messageObj" content="contentTemplate" :visible="isVisible" variant="Outlined"
                  severity="Warning" cssClass="e-content-center"
                  :showIcon="false">
            <template v-slot:contentTemplate>
              <p>Enter a valid age between 18 and 60</p>
              <ejs-button content="Dismiss" v-on:click="dismissClick"></ejs-button>
            </template>
    </ejs-message>
   </div>
</template>

<style>
 @import "../node_modules/@syncfusion/ej2-base/styles/material.css";
 @import "../node_modules/@syncfusion/ej2-vue-notifications/styles/message/material.css"; 
 .e-message
 {
   width: 300px;
 }
 .container
 {
   margin: 20px;
 }
 .inputDiv
 {
   margin-top: -19px;
   margin-left: 108px;
 }
</style>
 