# Saral-Web: Time Range Merger

A Node.js utility that merges discontinuous time ranges within a specified threshold.

## Requirements

- Node.js v14 or higher

## Installation

```bash
npm install
```

## Running

```bash
node index.js
```

## Testing

```bash
npm test
```

## Usage Example

```javascript
const { mergeTimeRanges } = require('./mergeTimeRanges');

// Example: Merge time ranges with a 1000ms threshold
const ranges = [[1, 100], [150, 200], [250, 300]];
const threshold = 1000;

const merged = mergeTimeRanges(ranges, threshold);
console.log(merged); // [[1, 300]]
```

## Function Details

**`mergeTimeRanges(ranges, threshold)`**

Merges time ranges that are separated by a gap less than or equal to the threshold value.

- **Parameters:**
  - `ranges` (Array<[number, number]>): Array of [start, end) time ranges (can be unsorted, may overlap)
  - `threshold` (number): Maximum gap in milliseconds allowed between ranges to be merged

- **Returns:** Array of sorted, non-overlapping merged ranges

## Example Cases

```javascript
// Simple merge
mergeTimeRanges([[1, 100], [150, 200]], 100);
// Returns: [[1, 200]]

// No merge - gap exceeds threshold
mergeTimeRanges([[1, 100], [300, 400]], 100);
// Returns: [[1, 100], [300, 400]]

// Overlapping ranges
mergeTimeRanges([[1, 200], [100, 250]], 0);
// Returns: [[1, 250]]
```
