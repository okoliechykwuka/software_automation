# Data-Driven Testing for PayNow

This section contains compositional skills for data-driven testing using Robot Framework for the PayNow application.

## Contents

- [qna.yaml](./qna.yaml): Contains question-answer pairs for data-driven testing skills
- [Example Test Cases](#example-test-cases)

## Example Test Cases

Here's an example of a data-driven test case for PayNow:

```robotframework
*** Settings ***
Documentation    Validate Merchant Is Unable To Process Transaction With More Than Due Amount for Specific Invoice
Test Template    Validate Transaction Amount Limit

*** Test Cases ***    Customer    Invoice Amount    Payment Amount    Expected Error
Exceed Invoice Amount    STERLING_COOPER    100    200    You can not pay more than is due on an invoice.

*** Keywords ***
Validate Transaction Amount Limit
    [Arguments]    ${customer}    ${invoice_amount}    ${payment_amount}    ${expected_error}
    Create Customer And Invoice    ${customer}    ${invoice_amount}
    Attempt Payment    ${payment_amount}
    Validate Error Message    ${expected_error}
```

For more examples and detailed keyword descriptions, refer to the [qna.yaml](./qna.yaml) file.