<p align="center">
<a href="https://docs.forestgiant.com/#iris" target="_blank"><img src="https://dl.dropboxusercontent.com/s/qkyl4fk4ra4z995/Iris-Logo-Horz-Grey.svg?dl=0" height="150" alt="Iris logo"/></a>
</p>

<p align="center">
<a href="https://docs.forestgiant.com/iris/api/?toggle=node" target="_blank"><img src="https://img.shields.io/badge/docs-iris%20api-20B2C6.svg" height="25" alt="Iris API Docs"/></a>   <a href="https://gitter.im/forestgiant/Lobby" target="_blank"><img src="https://img.shields.io/badge/chat-gitter-E1463D.svg" height="25" alt="Forest Giant on Gitter"/></a>
</p>

This package provides an IrisClient which can be used to communicate with an Iris server using the gRPC protocol and Node.js.  With the exception of the `Close` method, which finishes immediately, the methods of IrisClient make use of Promises to return response objects.

### Constructor
Used to obtain a new IrisClient object.
```
constructor(serverAddress, caFile) {...}
```

### Connect
Creates a unidirectional stream from the gRPC to this client.  You may pass in a function `errorCallback` to be called if there is an error with the gRPC server stream.  The returned promise object contains the session identifier.
```
connect(errorCallback) {...}
```


### Close
Cleans up the client's connection and nulls out some of the variables the client uses.
```
close() {...}
```

### SetValue
Makes a gRPC request to set the value for the given key on the specified source.  Returns a promise object that contains the value that was set.
```
setValue(source, key, value) {...}
```

### GetValue
Makes a gRPC request to retrieve the value for the given key on the specified source.  Returns a promise object that contains the returned value.
```
getValue(source, key) {...}
```

### RemoveValue 
Makes a gRPC request to remove the key-value pair for the given key on the specified source.  Returns a promise object that contains the session identifier as well as the source and key of the removed value.  
```
removeValue(source, key) {...}
```

### RemoveSource
Makes a gRPC request to remove the source and any key-value pairs contained within it.  Returns a promise object that contains the session identifier as well as the identifier of the removed source.
```
removeSource(source) {...}
```

### GetSources
Makes a gRPC request to retrieve an array of identifiers for known sources.  Returns a promised array of source identifiers.
```
getSources() {...}
```

### GetKeys
Makes a gRPC request to retrieve an array of keys for the given source.  Returns a promised array of keys contained in the given source.
```
getKeys(source) {...}
```

### Subscribe
Makes a gRPC request indicating that the client wishes to receive all updates for the given source.  This method expects to receive a callback function `handler` that will be invoked when an update is received for this source.  Subscribe returns a promsied object that contains the session identifier as well as the identifier of the subscribed source.
```
subscribe(source, handler) {...}
```

### SusbcribeKey
Makes a gRPC request indicating that this client wishes to receive all updates for the given source and key.  This method expects to receive a callback function `handler` that will be invoked when an update is received for this source and key.  SubscribeKey returns a promised object that contains the session identifier, the identifier of the subscribed source, and the key that was subscribed to.     
```
subscribeKey(source, key, handler) {...}
```

### Unsubscribe
Makes a gRPC request indicating that the client should stop realying updates for the given source to the specified handler.  Unsubscribe returns a promised object containing the session identifier and the identifier of the unsubscribed source.    
```
unsubscribe(source, handler) {...}
```

### UnsubscribeKey
Makes a gRPC request indicating that the client should stop realying updates for the given source and key to the specified handler.  UnsubscribeKey returns a promised object containing the session identifier and the identifier of the unsubscribed source.       
```
unsubscribeKey(source, key, handler) {...}
```
