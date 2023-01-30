# getFeeHistory

Returns a collection of historical gas information.

## Import

```ts
import { getFeeHistory } from 'viem'
```

## Usage

```ts
import { getFeeHistory } from 'viem'
import { publicClient } from '.'
 
const feeHistory = await getFeeHistory(publicClient, { // [!code focus:4]
  blockCount: 4,
  rewardPercentiles: [25, 75]
})
```

## Returns

[`FeeHistory`](/docs/glossary/types#TODO)

The fee history.

## Parameters

### blockCount

- **Type:** `number`

Number of blocks in the requested range. Between 1 and 1024 blocks can be requested in a single query. Less than requested may be returned if not all blocks are available.

```ts
const feeHistory = await getFeeHistory(publicClient, {
  blockCount: 4, // [!code focus]
  rewardPercentiles: [25, 75]
})
```

### rewardPercentiles

- **Type:** `number[]`

A monotonically increasing list of percentile values to sample from each block's effective priority fees per gas in ascending order, weighted by gas used.

```ts
const feeHistory = await getFeeHistory(publicClient, {
  blockCount: 4,
  rewardPercentiles: [25, 75] // [!code focus]
})
```

### blockNumber (optional)

- **Type:** `number`

Highest number block of the requested range.

```ts
const feeHistory = await getFeeHistory(publicClient, {
  blockCount: 4,
  blockNumber: 1551231n, // [!code focus]
  rewardPercentiles: [25, 75]
})
```

### blockTag (optional)

- **Type:** `'latest' | 'earliest' | 'pending' | 'safe' | 'finalized'`
- **Default:** `'latest'`

Highest number block of the requested range.

```ts
const feeHistory = await getFeeHistory(publicClient, {
  blockCount: 4,
  blockTag: 'safe', // [!code focus]
  rewardPercentiles: [25, 75]
})
```