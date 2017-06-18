<template>
    <div class="col-xs-12 col-sm-6">
        <ul class="list-group">
            <li
                class="list-group-item"
                v-for="(obj, i) in servers">

                Server #{{ obj.id }}
                <br>
                Status: {{ obj.status }}
                <br>
                <button v-on:click="showDetails(i)">Show Details</button>
            </li>
        </ul>
    </div>
</template>

<script>
  import { eventBus } from '../../main'

  export default {
    data: function() {
      return {
        servers: [
          { id: 1, status: 'Normal' },
          { id: 2, status: 'Pending' },
          { id: 3, status: 'Initializing' },
          { id: 4, status: 'Booting up' },
          { id: 5, status: 'Normal' }
        ]
      }
    },

    methods: {
      showDetails: function(id) {
        console.log(id);
        eventBus.$emit('onShowDetails', this.servers[id]);
      }
    },

    created() {
      eventBus.$on('onChangeServerStatus', (obj) => {
        
      });
    }
  }
</script>

<style>

</style>
