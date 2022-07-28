# Application Servers

## Stateless App server

* All servers don’t remember client sessions
  * Using server-side cache like Redis
  * Using self contained data coming with the request such as tokens payload, headers, request payload...

> ## Stateful App Server
>
> * Remember user sessions
>   * Hash table (or any other cache data structure) to remember which app server to routes to
>   * Sticky sessions
>   * More difficult to scale

## REST APIs

{% embed url="https://restfulapi.net/" %}

{% embed url="https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design" %}

{% embed url="https://hackernoon.com/restful-api-designing-guidelines-the-best-practices-60e1d954e7c9#comment-4865610272" %}

{% embed url="https://blog.restcase.com/rest-api-error-codes-101/" %}

