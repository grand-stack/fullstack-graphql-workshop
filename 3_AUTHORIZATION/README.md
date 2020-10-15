# Authorization

In this module we add authentication to our movies search GraphQL API using the `graphql-auth-directives` package and JSON Web Token (JWT).

## Overview

## GraphQL Auth Directives

By attaching 

Let's review the documentation for using `graphql-auth-directives` in the [GRANDstack docs.](https://grandstack.io/docs/neo4j-graphql-js-middleware-authorization)

### JWT

JSON Web Token (JWT) allows us to create cryptographically signed tokens that embed *claims*, expressed as a JSON payload.

We'll use the [JWT.io](https://jwt.io) online playground to create a JWT for our application.

## Exercise ⏲️ `5 minutes`

* Create a JWT using [JWT.io](https://jwt.io)
* Use random 256-bit key for for the signing key: `Dpwm9XXKqk809WXjCsOmRSZQ5i5fXw8N`
* Include the following payload, replacing `name` and `email`:

```
{
    "sub": "u1",
    "name": "William Lyon",
    "email": "will@grandstack.io",
    "iat": 1602765555
}

```

For example, here is the token generated using the above payload:

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJ1MSIsIm5hbWUiOiJXaWxsaWFtIEx5b24iLCJlbWFpbCI6IndpbGxAZ3JhbmRzdGFjay5pbyIsImlhdCI6MTYwMjc2NTU1NX0._gOShe-H1G1NR69s4dmlnjnrB1d88xsLGrKUU4f_poI
```

## Exercise ⏲️ `15 minutes`

* Protect the Business address field with the `@isAuthenticated` schema directive
* Query your GraphQL endpoint using GraphQL Playground to verify the address is protected.
* Protect the User type with the `@hasRole` directive, ensuring that only users with the role "admin" are able to access user information


## Cypher Params

We can use middleware to inject user specific information into Cypher queries defined in the `@cypher` schema directive. Let's review the documentation for this feature [here.](https://grandstack.io/docs/neo4j-graphql-js-middleware-authorization#cypher-parameters-from-context)

## Exercise ⏲️ `15 minutes`

Using the Cypher params functionality:

* Add a query field to return the currently authenticated user
* Add a mutation to add businesses to a user-specific "favorites" list
* Add a query field to return the list of favorited businesses for the currently authenticated user
