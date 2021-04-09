<template>
    <div>
      <h1>Slave</h1>
    </div>
</template>



<script>
import Gateway from '@nsoft/seven-gravity-gateway/slave';


let slave = Gateway({
    slaveId : 'GatewayPlayground',
    data : {test: "hello from slave"},
    load: function() {
      
    },
    allowedOrigins: '*',
    debug : true
});


slave.emit({
  data: {slave: 'hellooooo slave emit'},
  action : 'Betslip.Add',
}, '*');



export default {
  name: 'Slave',
  data() {
    return {
    }
  },
}

</script>
