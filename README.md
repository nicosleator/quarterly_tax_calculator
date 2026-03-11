# estimated-tax-calculator

Calculates quarterly estimated tax payments for a sole proprietor in New York City,
covering federal, NY state, and NYC taxes. Outputs both minimum and maximum quarterly
payments based on IRS safe harbor rules.

## Assumptions

This program assumes the filer is:
- Single, no dependents
- A NYC resident
- Operating as a sole proprietor
- Has investment income (capital gains, dividends, interest)
- Not a farmer or charitable organization

## Prerequisites

- R
- The following packages:
  - readr
  - dplyr
  - tibble

## Data

The program reads two `.rds` files that must be present in the working directory:

| File | Description |
|---|---|
| `quarterly_income.rds` | Quarterly business income |
| `quarterly_expences.rds` | Quarterly business expenses |

## Configuration

Update the following variables in the **Find AGI** section each year:
```r
long_term_capital_gain_loss  <- 0
short_term_capital_gain_loss <- 0
dividends_and_intrest        <- 0
```

And update these values each tax year as IRS thresholds change:
```r
standard_deducton  <- 15000   # standard deduction
cgtw_line_11       <- 48350   # 0% capital gains threshold
cgtw_line_19       <- 533400  # 15%/20% capital gains threshold
etw_line_12b       <- 6345    # prior year's federal tax
nys_line_a25       <- 1162    # prior year's NY state tax
nyc_line_b25       <- 825     # prior year's NYC tax
```

## Output

The program prints minimum and maximum quarterly payment estimates for federal,
NY state, and NYC taxes, as well as combined totals.

## ⚠️ Disclaimer

This program is not professional tax advice. It is a personal tool built to
assist with estimated tax calculations and may not account for all tax situations.
Consult a qualified tax professional before making payment decisions.
