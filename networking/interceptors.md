#TIL interceptors are a thing.

Interceptors are functions that get called before any HTTP request.
They're useful when you have to make a HTTP request for every request in your app, but don't want to repeat the code over and over.

Essentially it's middleware for HTTP requests.

Use cases:
- Authentication: before very API request, call an /auth endpoint to make sure the user is authenticated or authorized to use the resource.

I found this from Angular, apparently interceptors are built in. There aren't interceptors in React or fetch(), but you could use axios, which has a helper for intereceptors.

Stackoverflow link: https://stackoverflow.com/questions/31302689/react-native-http-interceptor
