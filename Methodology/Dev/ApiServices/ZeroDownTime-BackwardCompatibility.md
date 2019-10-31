# Zero Down Time Development - API backward compatibility

No, it's not only up to our awesome Blue Green algorithm to make a Zero Down-Time deployment, it's also up to the new code deployed.

The new code must still support the old API.

Imagine your client working on your cool Web Site. He got all the HTML and Javascript in his browser. He got data in his local storage.

While working on the website, a "Zero Down-Time" deployment has successfully finished in your production environment.
This new version, has changed an API signature in you API service and in the WebApp service, has changed the javascript to call the new API signature.

The client's browser still got the old Javascript, because he hasn't refreshed the browser. Of course, he gets an HTTP 404 mentioning that the API doesn't exist - Oops, it was really a "Zero Down-Time"

For Zero Down-time deployment, in case of breaking an API, you must do it in two steps, thus, in the first step support both of the APIs, until you got no client left that calls your old api. In step two, you stop supporting the old api.

- Also valid in clients that are not browsers
- It can be a real headache to support both APIs - stay strong
- Make it doesn't worth the headache in case you have few clients
  - If you do choose to break API without handling it right, choose the right time when activity is low, so returned clients will get the new version of the code. (Valid in browsers)
