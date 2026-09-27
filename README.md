# Scheme Calculator

A lightweight, browser-based calculator that estimates project cost,
eligible loan amount, scheme details, EMI, and a quarterly repayment
schedule from the user's available margin money.

## Features

-   Accepts available margin money in Indian rupees (₹).
-   Estimates total project cost using a 10% margin contribution
    assumption.
-   Calculates the corresponding 90% loan amount.
-   Selects a scheme tier based on the estimated project cost.
-   Displays the assumed interest rate, tenure, moratorium, and maximum
    loan amount.
-   Estimates monthly EMI, total interest, and total repayment.
-   Generates a quarterly repayment schedule showing principal,
    interest, and remaining balance.
-   Initially shows up to eight quarters, with an option to reveal the
    remaining schedule.
-   Formats currency values using the Indian numbering system.

## Tech Stack

-   HTML
-   CSS
-   Vanilla JavaScript

No framework, package installation, backend, or API key is required.

## Run Locally

1.  Save the HTML file as `index.html`.
2.  Open `index.html` in a modern web browser.
3.  Enter a positive amount in **Available Margin Money (₹)**.
4.  Select **Calculate** to view the results.

## Calculation Logic

The calculator currently uses the following assumptions:

-   Margin money is 10% of the total project cost.
-   Loan amount is 90% of the total project cost.
-   Project cost = available margin money ÷ 0.10.
-   Loan amount = project cost × 0.90.

### Scheme tiers encoded in the code

  --------------------------------------------------------------------------
  Estimated    Scheme        Interest       Tenure   Moratorium Maximum loan
  project cost label             rate                           used for EMI
  ------------ --------- ------------ ------------ ------------ ------------
  Up to        Micro        6.5% p.a.      3 years     3 months    ₹1,25,000
  ₹1,40,000    Finance                                          
               Scheme                                           

  Above        Term Loan      8% p.a.      7 years     6 months   ₹45,00,000
  ₹1,40,000    Scheme                                           
  and up to                                                     
  ₹50,00,000                                                    
  --------------------------------------------------------------------------

For EMI calculations, the code caps the calculated loan at the selected
tier's maximum loan. The summary displays both the calculated loan
amount and the capped amount used for repayment calculations.

The EMI calculation uses a monthly interest rate and subtracts the
moratorium months from the tenure to determine the number of
instalments. The schedule aggregates monthly principal and interest into
quarterly rows.

## Important Limitations

-   This is a basic, client-side calculator. It does not submit
    applications, contact lenders, or verify eligibility with a
    government agency.
-   Scheme names, rates, limits, margin assumptions, and moratorium
    periods are hardcoded in the HTML. They are assumptions in the
    current implementation and should be checked against current
    official scheme guidelines before real-world use.
-   The calculator does not currently implement the broader Mudra,
    PMEGP, or CGTMSE multi-scheme matching logic.
-   The displayed first payment date is an estimate based on the current
    date plus the moratorium period; actual repayment dates depend on
    lender terms and disbursement details.
-   The EMI logic treats the moratorium as a period before instalments
    begin. It does not separately model interest accrued or capitalized
    during the moratorium.
-   Invalid or empty input is not accompanied by a dedicated validation
    message in every case.

## Suggested Improvements

-   Add clear validation for empty, zero, negative, and non-numeric
    input.
-   Display a notice that results are estimates and require official
    verification.
-   Move scheme parameters into a separate configuration object so they
    can be updated more easily.
-   Add automated tests for project-cost, loan-cap, EMI, and
    repayment-schedule calculations.
-   Clarify how interest is handled during the moratorium and align the
    schedule with the applicable lender's rules.

## License

No license is specified. Add a license before distributing or reusing
the project if needed.
