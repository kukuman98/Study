# sens-v2-note

Base Bonus :

* bonus\_promotion
* discount\_promotion
* feedback\_promotion

Bonus\_Gift\_Promotion:

* promotion.value  attach to user.bonus

Cart\_api:

* Using repayment

Contact\_api:

* Using api.notification
* Using revns

Credit\_api:

* api.calc
* api.item
* api.manager ManagerCreateMixin\(manager class = OrderManager\)
* when create credit then using OrderManager to control Handler\(OrderMaster\) to create Order

Generic\_view:

* generic
* create model mixing
* update model mixing

Identity\_api:

* verify User token\(django\) to get user profile

invoice api:

* api.payment \(InvoiceOrder, InvoiceSDK, parse\_invoice\_config\)
* action type = manual issue

api.order\_api:

* inheritance payment’s order api List view
* \*\*很多東西

refund-do refund:

* using revpayment refund function
* 
manager:

* state machine event 

logistics:

* in api.model

orderitem:

* in api.model

order:

* in payment.model

invoice\_detail:

* in payment.model
* with revpayment is one to one relation

payment:

* in payment.model
* is record the checkout data

statemachine:

* manager state machine event using
* getattr to get function ,then call it
* event = getattr\(class, attribute name\)
* event\(\) \(function call\)

calculate:

* amount - tax include
* item amount - tax uninclude

item calculate:

* price - tax include
* amount - tax uninclude

invoice:

* B2B - uninclude tax
* B2C - include tax

