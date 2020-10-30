# Invoice

```text
from revpayment.invoice import InvoiceSDK 
from payment.models.order import Order 
order = Order.objects.last() 
sdk = InvoiceSDK(order) 
sdk.issue_invoice()
```

