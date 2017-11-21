# Circuit breakers

## Why

Circuit Breakers proxies consumption of a downstream system. They allow our services to "fail fast" in a predictable manner when downstream systems (such as BTO) return unhealthy responses. They will help to 

* provide your end users a better user experience
* prevent cascading failures across distributed services

## What
- [Martin Fowler on Circuit Breakers](https://www.martinfowler.com/bliki/CircuitBreaker.html)
- [A useful visual guide](https://www.bennadel.com/resources/uploads/2017/node-circuit-breaker.png)
- [Making the Netflix API more resilient](https://medium.com/netflix-techblog/making-the-netflix-api-more-resilient-a8ec62159c2d)

## How
You can write your own circuit breaker, or use an existing npm library - there are a few out there.
* [brakes](https://github.com/awolden/brakes) - supports both promise and callback style
* [circuit-breaker-js](https://github.com/yammer/circuit-breaker-js) - callback

A few guidelines:
* Return a useful error (for e.g. 503 Service Unavailable) in the fallback method when the circuit is open. 
* Don't use Auth Proxy (or in general, API gateways) for circuit breaking. Different services may have different needs for behaviour in the case that a circuit breaker is tripped, and as such control of this logic should be left to the service. 
 
