# Fullstack GraphQL Workshop

This workshop will be a hands-on session focused on building fullstack applications with Neo4j, GraphQL, JavaScript, and React. 

Before the session please install:

* Neo4j Desktop: https://neo4j.com/download/
* A recent version of Node.js (v12.x or later): https://nodejs.org/
* The npm package manager (v5.x or later, installed with Node.js by default), or yarn if you prefer: https://www.npmjs.com/get-npm

You can run the following commands to check if node and npm are installed:

```
node -v
npm -v
```

We will make use of the following resources and tools, so if you'd like to get a head start you can familiarize yourself with the following:

* Neo4j Sandbox: https://neo4j.com/sandbox/
* GraphQL Architect: https://install.graphapp.io/
* The create-grandstack-app CLI: https://grandstack.io/docs/getting-started-grand-stack-starter
* Netlify: https://www.netlify.com/

And for reference, the GRANDstack documentation: https://grandstack.io/

## [Module 1: Neo4j GraphQL](1_INTRO_TO_NEO4J_GRAPHQL)

In this module we take a look at Neo4j, GraphQL, and the Neo4j GraphQL integrations. First, we explore writing GraphQL queries against a demo GraphQL API of movies. Then we use the GraphQL Architect graph app for Neo4j Desktop to see how we can build our own GraphQL APIs using Neo4j GraphQL.

## [Module 2: GRANDstack](2_GRANDstack)

In this module we'll use the `create-grandstack-app` CLI to create a fullstack skeleton application using GraphQL, React, Apollo, and Neo4j Database. We'll then make some updates to the application to convert it to a movies search application using the Recommendations Neo4j Sandbox. Finally, we'll see how to deploy the application to Netlify.

## [Module 3: Authorization](3_AUTHORIZATION)

In this module we add authentication to our movies search GraphQL API using the `graphql-auth-directives` package and JSON Web Token (JWT).

Each module should take roughly 60-90 minutes to complete.

Let's [get started!](1_INTRO_TO_NEO4J_GRAPHQL)

