# node-lambda-graphql
AWS Lambda graphql handler

# Installation

```npm install --save lambda-graphql```

# Usage

1) create Lambda function in AWS console

2) install `lambda-graphql` and `graphql` modules

```npm install --save lambda-graphql graphql```

3) create `index.js`...for example:

```
'use strict'

const graphql = require('graphql')
const lambdaGraphql = require('lambda-graphql')

const schema = graphql.buildSchema(`
  type Query {
    hello: String
  }
`)

const root = {
  hello: function(params) {
    return 'world'
  }
}

exports.handler = lambdaGraphql({
  schema: schema,
  rootValue: root
})
```

3) deploy function by uploading to AWS Lambda

4) setup AWS Gateway API with proxy resource (for example /graphql) and forward requests (`GET` and `POST` methods) to created lambda function
