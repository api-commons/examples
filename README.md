# API Examples

API Examples are machine-readable request and response examples for the operations of an API, organized by operation and captured independently of the API definition itself. Good examples are one of the highest-leverage building blocks in API operations—they power documentation, drive mocking and testing, and give consumers concrete, copy-pasteable illustrations of how each operation actually behaves. This repo manages a common schema for describing those examples so they can be produced once and reused across tooling.

## API Commons

API Examples are an [API Commons](http://apicommons.org) building block—an open, machine-readable way to describe the examples used within APIs so they stay interoperable across documentation, mocking, and testing tools. The schema in this repo builds on the [Microcks](https://microcks.io) `APIExamples` specification, reusing a proven, tool-supported format rather than inventing a new one.

## What's in this repo

- [schema/apiexamples-json-schema.yml](schema/apiexamples-json-schema.yml) — The JSON Schema for an `APIExamples` document (based on the Microcks `mocks.microcks.io/v1alpha1` `APIExamples` specification).
- [examples/petstore-v1-examples.yaml](examples/petstore-v1-examples.yaml) — A worked example set for a REST Petstore service.
- [examples/petstore-1.0-examples.yaml](examples/petstore-1.0-examples.yaml) — A worked example set for a GraphQL Petstore API.

## The Schema

The [apiexamples-json-schema.yml](schema/apiexamples-json-schema.yml) defines an `APIExamples` document with the following top-level, required properties:

- **apiVersion** — The version of the APIExamples description (`mocks.microcks.io/v1alpha1`).
- **kind** — The kind marker for the document (`APIExamples`).
- **metadata** — Reference information about the API the examples relate to, requiring a `name` and a `version`.
- **operations** — A map of API operations, where each operation holds one or more named example items.

Each example item is either a **request/response pair** (with a `request` and a `response`) or a **unidirectional message** (with an `eventMessage`), supporting both request/response APIs and event-driven ones.

## Example

The [petstore-v1-examples.yaml](examples/petstore-v1-examples.yaml) file organizes examples by operation:

```yaml
apiVersion: mocks.microcks.io/v1alpha1
kind: APIExamples
metadata:
  name: org.acme.petstore.v1.PetstoreService
  version: v1
operations:
  getPets:
    All Pets:
      request:
        body: ""
      response:
        body:
          pets:
            - id: 1
              name: Zaza
```

## How It Fits

Examples are one of a growing set of API Commons building blocks that describe the business and technical realities of API operations in a machine-readable way. They complement definition-centric artifacts by supplying the concrete request/response data that documentation, mocking, and testing rely on, and they sit alongside building blocks like the [change log](https://github.com/api-commons/change-log), [road map](https://github.com/api-commons/road-map), [use cases](https://github.com/api-commons/use-cases), [guidance](https://github.com/api-commons/guidance), and [policies](https://github.com/api-commons/policies) within the APIs.json ecosystem.

## Support

This work is in an early stage of development and is rapidly moving as it is applied across a variety of user interfaces and approaches to API operations and governance. If you would like to contribute, have any questions, or would like to inform the work happening, please submit a GitHub issue on this repository or email kin@apievangelist.com.

## Part of API Commons

A machine-readable building block from **[API Commons](https://apicommons.org)** — open specifications and schemas for the APIs you produce and consume. See all building blocks and tools at **[apicommons.org](https://apicommons.org)** and the tools at **[apicommons.org/tools](https://apicommons.org/tools/)**.

**Related building blocks**
- [train-travel](https://github.com/api-commons/train-travel) — an APIs.json + OpenAPI template you can fork these examples against
- [json-api](https://github.com/api-commons/json-api) — JSON:API schemas and governance for standardizing API responses
- [problem-details-for-http-apis](https://github.com/api-commons/problem-details-for-http-apis) — RFC 9457/7807 error responses to pair with your examples
- [change-log](https://github.com/api-commons/change-log) — a machine-readable way to publish an API's changelog

## License

The artifacts in this repository — the schemas, examples, and API descriptions — are
licensed **[CC BY-NC-SA 4.0](LICENSE)** (Attribution–NonCommercial–ShareAlike).

API Commons licenses **artifacts** under CC BY-NC-SA 4.0 and **code** under Apache-2.0.
