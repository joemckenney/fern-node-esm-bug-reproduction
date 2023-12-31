# Dopt blocks JavaScript Node.js client

## Overview

The Dopt blocks JavaScript client is a friendly server-side package for accessing the Dopt blocks API to access and updates block and flow state for a particular user in Dopt.

It is published to npm as [`@dopt/blocks-javascript-node-client`](https://www.npmjs.com/package/@dopt/blocks-javascript-node-client).

## Installation

Via npm:

```bash
npm install @dopt/blocks-javascript-node-client
```

Via Yarn:

```bash
yarn add @dopt/blocks-javascript-node-client
```

Via pnpm:

```bash
pnpm add @dopt/blocks-javascript-node-client
```

## Configuration

To configure the blocks JavaScript client you will need

1. A blocks API key (generated in Dopt)
1. A block uid

## Usage

### Initialization

```ts
import { DoptApiClient } from '@dopt/blocks-javascript-node-client';

const client = new DoptApiClient({
  apiKey: process.env.DOPT_BLOCKS_API_KEY as string,
});
```

### Blocks

Get block data using the `getBlock` method:

```ts
const block = await client.blocks.getBlock('model-block-1', {
  version: 3,
  userIdentifier: 'example-user-idenitifer',
});
```

Transition a block using the `transition` method:

```ts
await client.blocks.transition('model-block-1', {
  version: 3,
  userIdentifier: 'example-user-identifier',
  transitions: 'complete',
});
```

### Flows

Get flow data using the `getFlow` method:

```ts
const flow = await client.flows.getFlow('example-flow-identifier', {
  version: 2,
  userIdentifier: 'example-user-identifier',
});
```

Transition a flow using the `flowIntent` method:

```ts
await client.flows.intent('example-flow-identifier', 'finish', {
  version: 3,
  userIdentifier: 'example-user-identifier',
});
```
