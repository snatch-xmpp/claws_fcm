Claws REST
===========

This claw is designed to use REST to perform HTTP requests to the servers and process the response via Snatch as an input from the server. It's a good solution to use when we want to perform a lot of requests and process the response in as events.

This claw should be started as follow:

```erlang
Params = #{domain => "localhost",
           schema => "http",
           max_sessions => 5,
           max_pipeline_size => 1,
           port => 80},
{ok, PID} = claws_kafka:start_link(Params).
```

This claw configures [ibrowse](https://github.com/cmullaparthi/ibrowse) to generate as many connections as needed and keep them alive if it's possible.

The params passed inside of the map for the `start_link/1` function are:

- `domain` the domain name where the request will be sent. In addition we use the domain to configure the max number of sessions and pipeline size (see below).
- `schema` (optional) we can choose to use http or https (default: http).
- `port` (optional) the port number to connect to (default: 80).
- `max_sessions` (optional) the maximum number of simultaneous sessions we support (default: 10).
- `max_pipeline_size` (optional) the maximum number of elements that could be waiting in the pipeline to be attended (default: 1).
