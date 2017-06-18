<template>
    <div class="col-xs-12 col-sm-6">
        <p>Server Details are currently not updated</p>
        <p v-if="myObj">Server Number: {{ myObj.id }} </p>
        <p v-if="myObj">Server Status: {{ myObj.status }}</p>

        <input  v-if="showButton === true"  v-model:value="myObj.status" type="text">
        <button v-if="showButton === true"  v-on:click="changeServerStatus" type="button" name="button"> Change Current Server Status</button>
    </div>

</template>

<script>
  import { eventBus } from '../../main'

  export default {

    data: function() {
      return {
        showButton: false,
        myObj: { id:'', status: 'none' }
      }
    },

    methods: {
      changeServerStatus: function() {
        eventBus.$emit('onChangeServerStatus', this.myObj);
      }
    },

    created: function() {
      eventBus.$on('onShowDetails', (data) => {
        this.showButton = true;
        this.myObj = data;
      });
    }
  }
</script>

<style>

</style>
