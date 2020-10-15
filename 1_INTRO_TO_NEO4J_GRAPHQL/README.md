# Intro To Neo4j GraphQL

## Overview

In this module we take a look at Neo4j, GraphQL, and the Neo4j GraphQL integrations. First, we explore writing GraphQL queries against a demo GraphQL API of movies. Then we use the GraphQL Architect graph app for Neo4j Desktop to see how we can build our own GraphQL APIs using Neo4j GraphQL.

## What is Neo4j?

![The Neo4j graph platform](img/graphplatform.png)

Neo4j is a native graph database with many features and functionality making up the Neo4j Graph Platform. Specifically:

* The Neo4j DBMS
* The property graph data model
* The Cypher query language
* Language drivers using the Bolt protocol for building applications
* Graph analytics with Graph Data Science
* Data visualization with Neo4j Bloom
* Neo4j Aura database-as-a-service
* A GraphQL integration for building GraphQL APIs backed by Neo4j

## What is GraphQL?

![What is GraphQL](img/graphqloverview.png)

GraphQL is an API query language and runtime for fulfilling those queries. GraphQL uses a type system to define the data available in the API, including what entities and attributes (*types* and *fields* in GraphQL parlance) exist and how types are connected (the data graph). GraphQL operations (queries, mutations, or subscriptions) specify an entry-point and a traversal of the data graph (the *selection set*) which defines what fields to be returned by the operation.


### Important GraphQL Concepts

#### GraphQL Type Definitions

GraphQL type definitions define the data available in the API. These type definitions are typically defined using the GraphQL Schema Definition Language (SDL), a language agnostic way of expressing the types. However, type definitions can be also be defined programmatically.

<img src="img/typedefs.png" width=500 />


#### GraphQL Operations

Each GraphQL operation is either a Query, Mutation, or Subscription. The fields of the Query, Mutation, and Subscription types define the entry points for an operation. Each operation starts at the field of one of these types.

<img src="img/operation.png" width=500 />


#### The Selection Set

The selection set specifies the fields to be returned by a GraphQL operation and can be thought of as a traversal through the data graph.

<img src="img/selectionset.png" width=500 />

The response to a GraphQL request matches the shape of the selection set.

<img src="img/result.png" width=500 />

#### Resolvers

In GraphQL resolvers are the functions responsible for actually fulfilling the GraphQL operation. In the context of a query, this means fetching data from a data layer.

<img src="img/resolvers.png" width=500 />


### Benefits of GraphQL

Some of the benefits of GraphQL include:

* **Overfetching** - sending less data over the wire
* **Underfetching** - everything the client needs in a single request
* The **GraphQL specification** defines exactly what GraphQL is
* **Simplify data fetching** with component based data interactions
* **"Graphs all the way down"** - GraphQL can help unify disparate systems and focus API interactions on relationships instead of resources.
* **Developer productivity** - By reasoning about application data as a graph with a strict type system developers can focus on building applications.


### GraphQL Challenges

Of course GraphQL is not a silver bullet. It's important to be aware of some of the challenges that come from introducing GraphQL in a system.

* Some well understood practices from REST don't apply
    * HTTP status codes
    * Error handling
    * Caching
* Exposing arbitrary complexity to the client and performance considerations
* The n+1 query problem - the nested nature of GraphQL operations can lead to multiple requests to the data layer(s) to resolve a request
* Query costing and rate limiting

Best practices and tooling have emerged to address all of the above, however it's important to be aware of these challenges.

## What is Neo4j GraphQL?

<img src = 'img/neo4jgraphql.png' width=100/>

The fundamental goal of the Neo4j GraphQL integrations is to make it easier to build GraphQL APIs backed by Neo4j.

> NOTE: It's important to point out that GraphQL is an API query language and NOT a database query language. The goal of the Neo4j GraphQL integration is to help build the API layer that sits between the client and database, not to execute GraphQL queries directly against the database.

At a high level the goals are:

* Reducing boilerplate
* Developer productivity
* Extensibility
* Performance

### Goals of Neo4j GraphQL

#### GraphQL First Development

GraphQL type definitions can drive the database data model, which means we don't need to maintain two separate schemas.

<img src="img/graphqlfirst.png" >

#### Auto-generate GraphQL CRUD API

This includes

* Query & Mutation types (an API entrypoint for each type defined in the schema)
* Ordering
* Pagination
* Complex filtering
* DateTime & Spatial types and filtering

<img src="img/crud.png" />

#### Generate Cypher From GraphQL Operations

To reduce boilerplate and optimize for performance Neo4j GraphQL automatically generates a single database query for any arbitrary GraphQL request. This means the developer does not need to implement resolvers and each GraphQL operation results in a single roundtrip to the database.

<img src="img/generate.png" />

#### Extend GraphQL With Cypher

To add custom logic beyond simple CRUD operations we can use the `@cypher` GraphQL schema directive to add computed fields bound to a Cypher query to the GraphQL schema.

<img src="img/cypher.png" />

## Neo4j GraphQL Implementations

There are multiple implementations of Neo4j GraphQL, in this workshop we focus on `neo4j-graphql.js`

![](img/implementations.png)

### `neo4j-graphql.js`

We will use `neo4j-graphql.js` to build GraphQL APIs in this workshop. `neo4j-graphql.js` is a JavaScript library designed to work with any Node.js GraphQL server.

<img src="img/neo4jgraphqljs1.png" />

The two main features provided by `neo4j-graphql.js` are 

1. Schema augmentation
1. GraphQL to Cypher transpilation

<img src="img/neo4jgraphqljs2.png" width=700 />

## Exploring The Movies GraphQL API

To familiarize yourself with GraphQL and writing GraphQL queries, explore the public movies GraphQL API at https://movies.grandstack.io. Open the URL in a web browser to access GraphQL Playground and explore the DOCS and SCHEMA tab to see the type definitions.

<img src="img/moviesapi.png" >

### Exercise ⏲️ `15 minutes`

Try writing queries to answer the following questions:

1. Find the titles of the first 10 movies, ordered by title.
1. Who acted in the movie "Jurassic Park"?
1. What are the genres of "Jurassic Park"? What other movies are in those genres?
1. What movie has the highest imdbRating?

## GraphQL Architect For Neo4j Desktop

GraphQL Architect is a Graph App for Neo4j Desktop that allows us to build, query, and deploy GraphQL APIs backed by Neo4j by writing only GraphQL SDL.

![](img/graphql-architect-usage1.png)

Read more about GraphQL Architect in [this article.](https://medium.com/neo4j/introducing-graphql-architect-19b0f2035e21)

### Installation And Usage

To install GraphQL Architect, first open Neo4j Desktop then open the Graph Apps Gallery:

![](img/graphql-architect-install1.png)

The Graph Apps Gallery allows you to install Graph Apps in Neo4j Desktop. Select the "Install" button for GraphQL Architect:

![](img/graphql-architect-install2.png)

Next, activate the database in Neo4j Desktop you'd like to use with GraphQL Architect, select the "Open" drop-down and choose "GraphQL Architect". You can also launch GraphQL Architect by clicking its icon in the Graph Apps drawer in Neo4j Desktop.

![](img/graphql-architect-install3.png)

This will launch the GraphQL Architect graph app. On first launch GraphQL Architect will inspect the data in your database and generate GraphQL type definitions for the data model.

![](img/graphql-architect-overview.png)

### Exercise ⏲️ `15 minutes`

Install, connect to Neo4j Sandbox.

1. Log in to Neo4j Desktop and launch a new "Blank" project.
1. Launch Neo4j Browser and run the command `:play grandstack` to load the GRANDstack browser guide
1. Click the query embedded in the GRANDstack browser guide and execute it to load our sample dataset
1. Connect this Sandbox instance to Neo4j Desktop by creating a new remote graph.
1. Install and launch the GraphQL Architect Graph App.
1. Start the local GraphQL server and navigate to the GraphiQL pane in GraphQL Architect.
1. Select the "Docs" tab to review the API schema.
1. Execute a GraphQL query to find all businesses and any reviews for each business.


### The Neo4j GraphQL API

Let's use the GraphiQL documentation tab to see how the following are added to the GraphQL schema:

* Query & Mutation fields
* Relationship fields
* Field arguments
* Filter arguments

### Exercise ⏲️ `10 minutes`

Write GraphQL mutations to accomplish the following:

1. Create a new Business node. You can make up a fake business or use your favorite store.
2. Connect this new business to a Category node
3. Add a Review for this business.

### `@cypher` Schema Directive

We can add custom logic to our API by using the `@cypher` GraphQL schema directive. Schema directives in GraphQL are used to indicate custom logic and the `@cypher` schema directive is used to bind a Cypher query to a computed field in the GraphQL schema.

Here we extend the Business type to include a computed field `average_stars`.

```GraphQL
extend type Business {
   average_reviews: Float @cypher(statement: "MATCH (this)<-[:REVIEWS]-(r:Review) RETURN avg(r.stars)")
}
```

The `@cypher` directive takes a single argument `statement` which is a Cypher query. The `this` Cypher variable is bound to the current object being resolved.

### Exercise ⏲️ `15 minutes`

In this exercise we will add a GraphQL field `recommended` to the User type that will be used to find businesses to recommend. We'll use the `@cypher` schema directive to map this field to a Cypher query.

1. Write a Cypher query to recommended businesses for a user. This could be done by looking at overlapping businesses reviewed, user ratings, graph algorithms using the Graph Data Science library or some other method. Feel free to be creative!
1. Add a new field `recommended` to the Movie GraphQL type definition that returns a list of Movie objects
1. Add the `@cypher` schema directive to the User type and adapt the Cypher statement so that it returns 

> Hint: Be sure to use the `this` keyword to refer to the currently resolved `User` node.


All done - that's it for this module! Let's [continue on to Module 2](2_GRANDstack) where we'll take a look at using neo4j-graphql.js in a fullstack application.



