---
description: This page contains cllie
---

# Clients

{% hint style="info" %}
**We have many types of client applications**

* Web / Browser
* Mobile
* API
* ...
{% endhint %}

## Web

### Caching

* CDN : to serve static assets such as HTML,CSS,JS, and media
* Local storage
  * You can't specify expiry as built-in but you can do it as an author `{“value”:””, createdAt:””}`
* Session storage
  * expire when you close the tab
  * it can be used to save UI State
* Cookies
  * User sessions
  * Authentication : Session ID or JWT
* Service workers and cache API : save responses to be used offline
* IndexedDB

### Network requests

* Retry
* Timeout
* Web socket
* HTTP pooling
* Error handling

### Performance

* Rendering
* Network bandwidth
* Compressing media
* Profiling

{% embed url="https://create-react-app.dev/docs/production-build/" %}

### Testing

* End-to-end
* A/B
* Automated UI Testing

{% embed url="https://www.cypress.io/" %}
