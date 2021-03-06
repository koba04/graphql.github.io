---
title: Execution
layout: ../_core/DocsLayout
category: API Reference
permalink: /docs/api-reference-execution/
next: /docs/api-reference-errors/
---

The `graphql/execution` module is responsible for the execution phase of
fulfilling a GraphQL request.

```js
import { execute } from 'graphql/execution'; // ES6
var GraphQLExecution = require('graphql/execution'); // CommonJS
```

## Overview

<ul class="apiIndex">
  <li>
    <a href="#execute">
      <pre>function execute</pre>
      Executes a GraphQL request on the provided schema.
    </a>
  </li>
</ul>

## Execution

### execute

```js
export function execute(
  schema: GraphQLSchema,
  documentAST: Document,
  rootValue?: any,
  variableValues?: ?{[key: string]: any},
  operationName?: ?string
): Promise<ExecutionResult>

type ExecutionResult = {
  data: ?Object;
  errors?: Array<GraphQLError>;
}
```

Implements the "Evaluating requests" section of the GraphQL specification.

Returns a Promise that will eventually be resolved and never rejected.

If the arguments to this function do not result in a legal execution context,
a GraphQLError will be thrown immediately explaining the invalid input.

`ExecutionResult` represents the result of execution. `data` is the result of
executing the query, `errors` is null if no errors occurred, and is a
non-empty array if an error occurred.
