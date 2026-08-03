
# Payment Dispute Reason

Reason for creating the dispute. Possible values:

- REFUND_NOT_PROCESSED: Customer claims that they returned goods or canceled services, but the Partner has not issued a refund to the Customer through the Acquiring Partners integration or Klarna's Partner Portal
- PRODUCTS_OR_SERVICES_NOT_RECEIVED: Customer claims that they did not receive the goods or services because the Partner was unwilling or unable to provide the goods or services
- PRODUCTS_DEFECTIVE_OR_NOT_AS_DESCRIBED: Customer claims that they received the goods or services, but that they deviated from what was advertised in terms of authenticity, condition or in other ways defective
- PURCHASE_HIGH_RISK: Klarna identified this transaction as high risk. Cancel the order if possible; if already shipped, provide tracking details and attempt to stop delivery. Response required within 96 hours.
- INCORRECT_AMOUNT: Customer claims to have received a charge for purchase that is incorrect, for example, missing discounts, unadvertised shipping fees at the time of purchase, incorrect items listed on the invoice, or an order amount already paid directly to the Partner outside of the Klarna Network
- PURCHASE_UNAUTHORIZED: Customer claims they have never made the purchase
- NON_COMPLIANCE: For transactions where Klarna has identified that the Partner has entered the Risk Program and is in Major Breach under Section 15.4 Partner Responsibilities and a Customer has not successfully disputed the transaction under another Dispute Type
- NON_GUARANTEED_PAYMENT_PROGRAM: Klarna identified that the transaction was not paid by the Customer and reverses the Claim to the Acquiring Partner. Only applicable to the "Debit Risk" Payment Program

## Enumeration

`PaymentDisputeReason`

## Fields

| Name |
|  --- |
| `REFUND_NOT_PROCESSED` |
| `PRODUCTS_OR_SERVICES_NOT_RECEIVED` |
| `PRODUCTS_DEFECTIVE_OR_NOT_AS_DESCRIBED` |
| `INCORRECT_AMOUNT` |
| `PURCHASE_HIGH_RISK` |
| `PURCHASE_UNAUTHORIZED` |
| `NON_COMPLIANCE` |
| `NON_GUARANTEED_PAYMENT_PROGRAM` |

## Example

```python
from klarna.models.payment_dispute_reason import PaymentDisputeReason

payment_dispute_reason = PaymentDisputeReason.PURCHASE_HIGH_RISK
```

