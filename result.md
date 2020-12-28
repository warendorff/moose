---
layout: default
---

# The formula

`floor(round((($propertyValue / 320)) * $lookupValue * $factor, 2))`

1. Use property-price (e.g. 400 for BT, which is #22) and divide by 320 to determine `$propertyFactor`
2. Use lookup-table above to determine the `$lookupValue` 
3. Use factor-table to determine `$factor`
4. Multiply `$propertyFactor` with `$lookupValue` and `$factor`, round by 2 decimals
5. Round down value to a whole number
6. The price per share will fluctuate between +6 and -6

## Example

For example, the current situation on orange (TGI Fridays, Pizza Hut & Burger King) as it would display on the machine:

| Propertynumber | Buildings | Stock left | Player 1 | Player 2 | Player 3 | Player 4 | Player 5 | Player 6 | €M +/- |
|----------------|-----------|------------|----------|----------|----------|----------|----------|----------|--------|
|             09 |         2 |          4 |        5 |          |          |          |          |          |     98 | 
|             10 |         2 |          0 |        5 |        3 |        1 |          |          |          |    146 | 
|             11 |         3 |          4 |        5 |        2 |          |          |          |          |    152 | 

- For TGI Fridays: `(180 / 320) * 10 * 17 = 95,625` so price will flucuate between 89 and 101.
- For Pizza Hut: `(180 / 320) * 15 * 17 = 143,4375` so price will flucuate between 137 and 149.
- For Burger King: `(200 / 320) * 12 * 20 = 150` so price will flucuate between 144 and 156.

# Data

## Property values

| property | value |
|----------|-------|
|        1 |    60 |
|        1 |    60 |
|        2 |    60 |
|        3 |   100 |
|        4 |   100 |
|        5 |   120 |
|        6 |   140 |
|        7 |   140 |
|        8 |   160 |
|        9 |   180 |
|       10 |   180 |
|       11 |   200 |
|       12 |   220 |
|       13 |   220 |
|       14 |   240 |
|       15 |   260 |
|       16 |   260 |
|       17 |   280 |
|       18 |   300 |
|       19 |   300 |
|       20 |   320 |
|       21 |   350 |
|       22 |   400 |

## The lookup table

| players\shares |  1 |  2 |  3 |  4 |  5 |  6 |  7 |  8 |  9 |
|----------------|----|----|----|----|----|----|----|----|----|
|              1 |  6 |  7 |  8 |  9 | 10 | 10 | 10 | 10 | 10 |
|              2 |    |  8 |  9 | 10 | 11 | 12 | 12 | 12 | 12 |
|              3 |    |    | 10 | 11 | 12 | 13 | 14 | 14 | 15 |
|              4 |    |    |    | 12 | 13 | 14 | 15 | 16 | 17 |
|              5 |    |    |    |    | 14 | 15 | 16 | 18 | 20 |
|              6 |    |    |    |    |    | 16 | 18 | 20 | 23 |

## The factor

| value       | factor |
|-------------|--------|
| no monopoly |      7 |
| monopoly    |     12 |
| 1 building  |     14 |
| 2 builings  |     17 |
| 3 buildings |     20 |
| 4 buildings |     22 |
| 5 buildings |     28 |
