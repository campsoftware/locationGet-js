# locationGet-js

Calling Example:

locationGet( function ( coords ) { alert( coords['ErrorCode'] + '|' + coords['Latitude'] ); } );

```javascript
function locationGet( callbackFunction ) {                                                                  
    // Calling Example                                                                                      
    // locationGet( function ( coords ) { alert( coords['ErrorCode'] + '|' + coords['Latitude'] ); } );     
    if ( navigator.geolocation ) {                                                                          
        navigator.geolocation.getCurrentPosition(                                                           
            function ( position ) {                                                                         
                let result = {};                                                                            
                result[ 'ErrorCode' ] = "0";                                                                
                result[ 'ErrorDesc' ] = "";                                                                 
                result[ 'Latitude' ] = position.coords.latitude;                                            
                result[ 'Longitude' ] = position.coords.longitude;                                          
                result[ 'Altitude' ] = position.coords.altitude;                                            
                result[ 'Heading' ] = position.coords.heading;                                              
                result[ 'Speed' ] = position.coords.speed;                                                  
                result[ 'Accuracy' ] = position.coords.accuracy;                                            
                result[ 'AccuracyAltitude' ] = position.coords.altitudeAccuracy;                            
                callbackFunction( result );                                                                 
            },                                                                                              
            function ( err ) {                                                                              
                let result = {};                                                                            
                result[ 'ErrorCode' ] = err.code;                                                           
                result[ 'ErrorDesc' ] = err.message;                                                        
                callbackFunction( result );                                                                 
            },                                                                                              
            {                                                                                               
                enableHighAccuracy: true,                                                                   
                timeout: 15000,                                                                             
                maximumAge: 0                                                                               
            }                                                                                               
        )                                                                                                   
    } else {                                                                                                
        let result = {};                                                                                    
        result[ 'ErrorCode' ] = -1;                                                                         
        result[ 'ErrorDesc' ] = "Browser does not support Geolocation";                                     
        callbackFunction( result );                                                                         
    }                                                                                                       
}      
```
