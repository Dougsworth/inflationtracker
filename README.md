# My Inflation Rate 🇯🇲

Jamaica's headline inflation rate is an average of everybody's basket. This tool works out
**your** rate from what you actually spend, using STATIN's latest published rate for each
CPI division.

**Live:** _(add your Vercel URL here after the first deploy)_

## How it works

You enter nine monthly figures. Each one is deflated by its own division's 12-month
point-to-point inflation rate to get what that line cost a year ago:

```
last_year_basket = Σ ( spend_i / (1 + rate_i) )
your_rate        = (this_year_basket / last_year_basket) - 1
```

Each category's contribution in percentage points is `(spend_i - last_year_i) / last_year_basket`,
so the drivers shown always sum back to your headline rate. The salary figure is simply
this year's basket grown by your rate (plus an optional real-growth target).

Nothing is sent anywhere — the maths runs in the browser and no data leaves the device.

## Data

| Division | 12-month rate |
|---|---|
| Food & non-alcoholic beverages | 10.2% |
| Transport | 14.6% |
| Housing, water, electricity, gas | 4.8% |
| Furnishings & household items | 3.4% |
| Health | 3.9% |
| Recreation, sport & culture | 3.2% |
| Clothing & footwear | 2.9% |
| Alcohol & tobacco | 6.7% |
| Other goods & services | 4.5% |
| **National (all items)** | **7.9%** |

Source: STATIN Consumer Price Index, August 2026.

**To refresh:** STATIN publishes the CPI monthly. Update the `rate` values in the `CATS`
array and the `HEADLINE` constant in `index.html`, plus the month label in the hero copy.

## Stack

Plain HTML, CSS and JavaScript. No build step, no dependencies, no tracking.

## Deploy

Static site — Vercel serves it as-is.

```bash
npx vercel          # preview
npx vercel --prod   # production
```

Or drag this folder onto https://vercel.com/new.
# inflationtracker
