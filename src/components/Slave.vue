<template>
    <div>
      <h1>Slave</h1>
      <button @click="msgToMaster">Send to Master</button>
    </div>
</template>



<script>
import Gateway from '@nsoft/seven-gravity-gateway/slave';


let slave = Gateway({
    slaveId : 'GatewayPlayground',
    data : {test: "hello from slave"},
    load: function() {},
    allowedOrigins: '*',
    debug : true,
});


slave.on('helloSlave', (event) => console.log(event.data))

export default {
  name: 'Slave',
  methods: {
    msgToMaster() {
      slave.emit({
       data: {slaveMessage: 'slave message to master'},
       action : 'helloMaster',
    }, '*');
    }
  }
}

</script>
