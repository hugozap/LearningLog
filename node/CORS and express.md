
# Disabling CORS in express

The server was not adding the correct list of authorized headers ,
specifically cache-control. Solution, add this middleware to express

app.use(function(req, res, next) {
  res.header("Access-Control-Allow-Origin", "*");
  res.header("Access-Control-Allow-Methods","POST, GET, OPTIONS");
  res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept, Cache-Control");
  next();
});

There are some special conditions that activate preflight.

https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS