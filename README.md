# Curbside Gateway Server

## What it is
This app is a simple express proxy for `curbside-react`; intercepting API calls from the front-end, to this backend; we can then make backend calls to other services, such as `curbside-api`, without the need for complicated CORS configuration.

## How it works
Simple express endpoints intercept requests, make a node-fetch request to the configured API, retrieve the result and pass it back to the front end.

The magic happens with the `curbside-react` `proxy` configuration in `package.json`. It should be pointing to this app.

Any other traffic is then forwarded to the react app.

During development, create a symbolic link to `curbside-react` in the root directory, in order to include it as part of servable elements.

An `npm run build` will actually build the react portions, and copy it's elements to this folder; the embedded express server then serves up that content whenever there is a request for a non-api related request (.js, images, and the like).

## Whois
Copyright (c) 2020, Four And A Half Giraffes, Ltd.