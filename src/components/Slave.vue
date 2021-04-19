<template>
    <div>
      <h1>Slave</h1>
      <button @click="msgToMaster">Send to Master</button>
      <button @click="asyncMsgToMaster">Async Message</button>
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

slave.on('helloSlave', (event) => console.log(event.data.masterMessage))

export default {
  name: 'Slave',
  methods: {
    msgToMaster() {
      slave.emit({
       data: {slaveMessage: 'slave message to master'},
       action : 'helloMaster',
      }, '*');
    },
    asyncMsgToMaster() {
      slave.emitAsync({
        action : 'asyncMess',
      }).then(function(res) {
        console.log(res)
      })
      .catch(function(err){
        console.log(err)
      });
    }
  }
}

</script>
