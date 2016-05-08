# Upload files to express

Install multipary module

https://www.npmjs.com/package/multiparty

```javascript
 // Inside the route: 
    var form = new multiparty.Form();
 
    form.parse(req, function(err, fields, files) {
      ...
    });
 ```