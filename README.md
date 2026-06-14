# Runway Model

**Know exactly how long your runway is.**

An [Aonami Labs](https://labs.aonamitech.com) open-source tool. Enter your monthly revenue, expenses, and cash balance — get burn rate, runway in months, break-even timeline, a 12-month cash flow projection, three forward scenarios, and a board-ready financial narrative. Runs entirely in your browser.

```
Financials  →  Burn rate  →  Runway in months  →  Break-even timeline  →  Board narrative
```

---

## What It Does

### Core Metrics

Runway Model calculates five critical numbers every founder needs:

| Metric | Formula | Why It Matters |
|--------|---------|----------------|
| **Net Burn/Month** | Expenses − Revenue | How fast you're burning cash |
| **Runway** | Cash balance ÷ Burn rate | How many months until you run out |
| **Break-even** | When Revenue = Expenses (at growth rate) | When you stop burning cash |
| **Default Date** | Today + (Runway × 30 days) | The day cash runs out if nothing changes |
| **Scenarios** | Base / +20% rev / −20% rev | How sensitive is runway to revenue? |

---

## How to Use

### Input

Four numbers. That's it.

```
Cash balance:      $5,000,000      (bank account today)
Monthly revenue:   $800,000        (incoming money)
Monthly expenses:  $1,200,000      (outgoing money)
MoM growth rate:   8%              (expected revenue growth per month)
```

### Output

Runway Model generates:

1. **Four KPI cards** — Net burn, runway, break-even, default date
2. **Runway bar** — Visual timeline from "now" to when cash runs out
3. **Scenario cards** — Base, optimistic (+20%), conservative (−20%)
4. **12-month projection table** — Month-by-month cash balance
5. **Board narrative** (optional AI) — Plain-English financial summary

### Steps

1. **Enter your numbers** — Results update live as you type
2. **Review the metrics** — Burn rate, runway in months, break-even date
3. **Run scenarios** — See how sensitive runway is to revenue changes
4. **Read the projection** — Month-by-month cash balance for next 12 months
5. **Generate narrative** (optional) — Add your API key for board-ready summary

---

## Features

### Live Calculation
- Results update as you type (no "Calculate" button)
- Change any number and see the impact instantly

### Multi-Currency
- INR (₹), USD ($), EUR (€)
- Switch currencies without re-entering data

### Scenario Analysis
- **Base case:** Your current trajectory
- **Optimistic:** Revenue +20% month-over-month
- **Conservative:** Revenue −20% month-over-month
- See how runway changes under each

### 12-Month Projection
- Month-by-month breakdown
- Revenue growth modeled at your specified rate
- Cash balance tracked from month 1 to month 12
- Break-even month highlighted (if reached)
- Default month highlighted (when cash hits zero)

### Visual Timeline
- Runway bar shows when cash runs out
- Color-coded: green (safe) → amber (caution) → red (urgent)
- Break-even date marked when applicable

### Board-Ready AI Narrative (BYOK)
- With your API key (Anthropic, OpenAI, Google, or Groq):
  - 3-paragraph financial summary
  - Current position → Growth trajectory → Key levers
  - Ready to paste into board deck

---

## Key Concepts

### Burn Rate
The amount of cash you burn per month = Expenses − Revenue

- **Positive burn:** Spending more than you earn (normal for growth stage)
- **Negative burn:** Revenue exceeds expenses (cash flow positive)
- **Zero burn:** Break-even

### Runway
How many months of cash you have left at your current burn rate = Cash balance ÷ Burn rate

- **18+ months:** Safe zone (time to course-correct)
- **12–18 months:** Caution zone (start fundraising)
- **6–12 months:** Urgent (fundraising must happen now)
- **< 6 months:** Critical (pivot or close)

### Break-even
The point at which revenue equals expenses. This is where burn rate becomes zero.

Runway Model calculates when break-even will occur *if* your revenue grows at the rate you specify.

Formula: `break_even_months = log(expenses / revenue) / log(1 + growth_rate)`

Example: If you're at $500K revenue, $1.2M expenses, growing 8% per month:
- Break-even ≈ 13 months from now
- If your runway is 10 months, you're in trouble (won't reach break-even before running out)

### Default Date
The exact calendar date when your cash hits zero at your current burn rate.

Example: If you have $5M, burning $400K/month:
- Runway: 12.5 months
- Default date: December 15, 2026 (assuming June 1, 2026 today)

---

## Scoring Examples

### Healthy Startup
```
Cash:      $3,000,000
Revenue:   $1,000,000/mo
Expenses:  $1,200,000/mo
Growth:    10%/mo

Net burn:       -$200K/mo   (revenue growing faster than expenses)
Runway:         ∞           (cash flow positive)
Break-even:     Already here
Status:         ✓ Sustainable
```

### Growth-Stage Startup
```
Cash:      $5,000,000
Revenue:   $800,000/mo
Expenses:  $1,200,000/mo
Growth:    8%/mo

Net burn:       $400K/mo    (burning cash steadily)
Runway:         12.5 months (safe but tightening)
Break-even:     ~13 months  (reachable before runway ends)
Status:         ⚠ Feasible if growth holds
```

### Pre-Revenue Startup
```
Cash:      $2,000,000
Revenue:   $0/mo
Expenses:  $500,000/mo
Growth:    N/A

Net burn:       $500K/mo    (pure burn)
Runway:         4 months    (critical)
Break-even:     N/A         (no revenue)
Status:         🔴 Urgent (fundraise now)
```

---

## How the Calculation Works

### Burn Rate
```
Net burn = Expenses − Revenue
```

### Runway (at constant burn)
```
Runway (months) = Cash balance / Monthly burn
```

### Break-even (with growth)
```
Break-even month = log(Expenses / Revenue) / log(1 + Monthly growth rate)
```

If the equation doesn't converge (no positive growth), break-even is N/A.

### 12-Month Projection
For each month `n` from 1 to 12:
```
revenue[n] = starting_revenue * (1 + growth_rate) ^ n
cash[n] = cash[n-1] - (expenses - revenue[n])
```

If `cash[n]` hits zero before month 12, projection stops there.

---

## Scenarios Explained

### Base Case
Your inputs as-is. Revenue grows at your specified rate, expenses stay constant.

### Optimistic (+20% revenue)
Same burn, but revenue is 20% higher at every point. Shows how much runway you gain if customers come faster than expected.

### Conservative (−20% revenue)
Revenue is 20% lower at every point. Shows your runway if growth slows or you lose customers.

**Why scenarios matter:** If your base-case runway is 12 months but the conservative scenario gives you only 4 months, you're fragile. Small revenue changes kill you.

---

## Disclaimer

Runway Model performs math on the numbers you enter. It **does not**:
- Predict whether your revenue growth rate is realistic
- Account for seasonal variation, one-time costs, or irregular expenses
- Model fundraising timing or dilution
- Predict product-market fit or customer acquisition
- Include capital-intensive milestones (hiring, infrastructure, launches)

**Treat it as a math tool, not a fortune teller.** The input numbers determine the output. If your assumptions are wrong, your runway prediction is wrong. Stress-test your growth rate assumptions with your team.

---

## BYOK AI

Add your own API key for optional board-ready narrative:
- **Anthropic** (Claude Sonnet/Opus)
- **OpenAI** (GPT-4o)
- **Google** (Gemini 2.0 Flash)
- **Groq** (Llama 3.3 70B)

Your key stays in your browser tab and is sent only to your chosen provider — never to Aonami.

---

## License

MIT © Aonami Labs. See [LICENSE](LICENSE).

---

## Suggested Reading

- **"The Lean Startup"** by Eric Ries — cash and burn rate are core to lean thinking
- **Y Combinator's Burn Rate guide** — how to think about sustainable burn
- **"Venture Deals"** by Brad Feld & Jason Mendelson — how VCs look at runway when deciding
- **CFO.com's cash flow primer** — finance fundamentals for non-finance founders

---

## Next Steps

1. **Enter your current numbers** — Cash, revenue, expenses, growth rate
2. **Check your runway** — How many months do you have?
3. **Run scenarios** — What if revenue grows slower than you expect?
4. **Plan your milestones** — What needs to happen before break-even?
5. **Board prep** — Use the narrative for your next investor conversation

---

**Runway Model** is a calculator. Real financial health also requires: product-market fit, customer retention, cost discipline, and a plan to reach profitability. Use this to track the math; use your instincts to drive the business.
