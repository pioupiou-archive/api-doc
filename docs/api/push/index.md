# Push API

Documentation for Push API is coming in few days...

```
<script src="http://api.pioupiou.fr/socket.io/socket.io.js"></script>
<script>
  var socket = io.connect('http://api.pioupiou.fr/v1/push');
  
  socket.on("connect", function () {
    socket.emit("subscribe", "all");
    socket.emit("subscribe", 1); // station n° 1
    //socket.emit("unsubscribe", "all");
  });
  
  socket.on("error", function (data) {
    console.log(data);
  });
  socket.on("status", function (data) {
    console.log(data);
  });
  socket.on("measurement", function (data) {
    console.log(data);
  });
  socket.on("location", function (data) {
    console.log(data);
  });

  
</script>
```