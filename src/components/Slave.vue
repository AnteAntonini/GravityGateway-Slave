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
    load: function(data) {
      console.log('slave load', data)
    },
    allowedOrigins: '*',
    debug : false
});


slave.emit({
  action : 'Betslip.Add',
}, '*');


export default {
  name: 'Slave',
  data() {
    return {
    
    }
  }

}

</script>
