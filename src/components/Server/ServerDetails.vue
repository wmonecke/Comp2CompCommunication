<template>
    <div class="col-xs-12 col-sm-6">
        <p>Server Details are currently not updated</p>
        <p>Server Number: {{ obj.id }} </p>
        <p>Server Status: {{ obj.status }}</p>
        <button v-if="showButton === true" type="button" name="button"> Change Current Server Status</button>

    </div>

</template>

<script>
  import { eventBus } from '../../main'

  export default {
    props: {
      data: Object
    },
    data: function() {
      return {
        showButton: false,
        obj: { id: "none", status: "unavailable"}
      }
    },

    created: function() {
      eventBus.$on('onShowDetails', (data) => {
        this.showButton = true;
        this.obj = data;
      });
    }
  }
</script>

<style>

</style>
