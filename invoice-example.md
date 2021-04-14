# Invoice Example

### How to use Invoice Issue api

```python
def perform_create(self) -> None:
        issue_url = f"https://payment.revtel-api.com/v3/invoice/issue"
        headers = {"Accept": "application/json", "x-api-key": settings.CLIENT_SECRET} # Your API_KEY
        data = self.build_invoice_data()    # build the issue invoice format
        url = add_url_query(
            issue_url,
            client_id=xxx,    # Your client_id
            client_secret=xxx,    # Your API_KEY
        )
        # url = 'https://payment.revtel-api.com/v3/invoice/issue?client_id=xxx&client_secret=xxx
        resp = requests.post(url, headers=headers, json=data)
        print(resp.json())    # Your can log the message to confirm invoice execute
```

### Invoice issue data format

```python
neweb Example
{
    "RespondType": "JSON",
    "Version": "1.4",
    "TimeStamp": str(
        int(datetime.now().replace(tzinfo=timezone.utc).timestamp())
    ),
    "MerchantOrderNo": "order_id",
    "Status": "1",
    "BuyerName": "buyer name",
    "BuyerEmail": "buyer email",
    "TaxType": "1/2/3/9",
    "TaxRate": float(5),
    "Amt": "cart amount (no tax)",
    "TaxAmt": "cart tax amount",
    "TotalAmt": "cart amount",
    "Category": "B2C or B2B",
    "PrintFlag": "N/Y", # if B2B then Y, if B2C and donation then Y, if B2C not donation then N
    "CarrierType": "0/1/2", # 0: mobile, 1: npc, 2: default
    "CarrierNum": "xxx" # if carrier_type=0 or 1, else can use email 
    "items": items,
}
```

* [Carrier Number Format](https://www.einvoice.nat.gov.tw/home/Article!showArticleDetail?articleId=1448444984179)
* items format

```python
[{
    "name": "item name",
    "quantity": "item quantity(int)",
    "price": "item identity price(int)",
    "amount": "item amount(int)",
},{
    "name": "item name",
    "quantity": "item quantity(int)",
    "price": "item identity price(int)",
    "amount": "item amount(int)",
}, ....
]
```



