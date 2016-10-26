# Ajax Request

This blog explain Ajax Request in Angular2, JQuery And Vanila JavaScript

#AngularJS

1. then have 1st successCallback and 2nd errorCallback:
   ```
   $http({
      method: 'POST', 
      url: '/someUrl',
      headers: { 'Content-Type': dataType }, 
      data: { test: 'test' }
   }).then(function successCallback(response) {}, function errorCallback(response) {});
   ```

2. Short cut:
   ```
   $http.get('/someUrl', config).then(successCallback, errorCallback); 
   $http.post('/someUrl', data, config).then(successCallback, errorCallback);

   $http.get('/someUrl', config).success(successCallback).error(errorCallback); 
   $http.post('/someUrl', data, config).success(successCallback).error(errorCallback);
   ```
   > Post call have body as data.
   
3. Abort Request:
   

#Jquery:

1. then have 1st successCallback and 2nd errorCallback, and success property too have successCallback, which will call first.
   ```
   $.ajax({
      type: "POST",
      url: 'someUrl', 
      dataType: dataType , 
      data: data, 
      success: success1Callback
   })
   .done(function success2Callback() { alert( "second success" ); })
   .fail(function errorCallback() { alert( "error" ); })
   .always(function() { alert( "finished" ); });
   ```

2. Short cut:
   ```
   $.get('/someUrl', config).done(successCallback).fail(errorCallback); 
   $.post('/someUrl', data, config).done(successCallback).fail(errorCallback);
   ```
   > Post call have body as data.

3. Abort Request:
   ```
   var request = $.ajax({
     type: "POST",
     url: 'someUrl', 
     dataType: dataType , 
     data: data, 
     success: success1Callback
   });
   request.done(function success2Callback() { alert( "second success" ); })
   request.fail(function errorCallback() { alert( "error" ); });
   
   request.abort();
   ```
   
#JavaScript

1. SynchronousRequest:
   ```
   function httpGet(theUrl) { 
      var xmlHttp = new XMLHttpRequest(); 
      xmlHttp.open( "GET", theUrl, false); // false for synchronous request 
      xmlHttp.send( null ); 
      return xmlHttp.responseText; 
   }
   ```

2. Asynchronous Request:
   ```
   function httpGetAsync(theUrl, callback) { 
      var xmlHttp = new XMLHttpRequest(); 
      xmlHttp.onreadystatechange = function() { 
            if (xmlHttp.readyState == 4 && xmlHttp.status == 200) callback(xmlHttp.responseText); 
      } 
      xmlHttp.open("GET", theUrl, true); // true for asynchronous 
      xmlHttp.send(null); 
   }
   ```